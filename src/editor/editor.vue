<template>
    <div class="external-components-wrapper">
        <div class="email-wrapper">
            <email :schema="schema"
                   :label="template.emailLabel"
                   :placeholder="template.emailPlaceholder"
                   :$v="$v">
            </email>
        </div>
        <div class="password-wrapper">
            <password :schema="schema"
                      :label="template.passwordLabel"
                      :placeholder="template.passwordPlaceholder"
                      :$v="$v">
            </password>
        </div>
    </div>
</template>
<script>
    import * as _ from 'lodash';
    import {validators} from '_validators';
    import email from './email.vue';
    import password from './password.vue';

    const {required, jsExpressionNonEmptyString, generateValidators} = validators;

    export default {
        name       : 'editor-test-example',
        props      : ['template', 'schema', 'step', 'stepId', 'steps', 'readonly'],
        components : {email, password},
        computed   : {},

        created () {},

        data () {
            return {};
        },

        methods : {},

        validations () {
            return {
                schema : validator(this.template)
            };
        }

    };

    export const data = (template) => ({
        email               : '',
        emailPlaceholder    : template.emailPlaceholder,
        emailLabel          : template.emailLabel,
        password            : '',
        passwordPlaceholder : template.passwordPlaceholder,
        passwordLabel       : template.passwordLabel,
    });

    export const validator = (template) => {
        return {
            email    : generateValidators(template.validateRequired, {required}),
            password : generateValidators(template.validateRequired, {required}),
        };
    };

    export const meta = {
        name    : 'test-external-component',
        type    : 'onereach-studio-form-editor',
        version : '1.0'
    };
</script>

<style scoped lang="scss" rel="stylesheet/scss">
    @import '../scss/colors.scss';

</style>


<style lang="scss" rel="stylesheet/scss">
    @import '../scss/colors.scss';

</style>
