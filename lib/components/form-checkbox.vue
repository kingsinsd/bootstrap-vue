<template>
    <label :class="[inputClass,checkboxClass,custom?'custom-checkbox':null]">
        <input
                type="checkbox"
                :id="id || ('b_'+_uid)"
                :name="name"
                :value="value"
                :disabled="disabled"

                :class="[custom?'custom-control-input':null]"
                :checked="checked===value"
                @change="$emit('change',$event.target.checked?value:uncheckedValue)"
        >
        <span class="custom-control-indicator" v-if="custom"></span>
        <span :class="[custom?'custom-control-description':null]"><slot></slot></span>
    </label>
</template>

<script>
    import formMixin from '../mixins/form';
    import formCheckBoxMixin from '../mixins/form-checkbox';

    export default {
        mixins: [formMixin, formCheckBoxMixin],
        model: {
            prop: 'checked',
            event: 'change'
        },
        props: {
            value: {
                default: true
            },
            uncheckedValue: {
                default: false
            },
            checked: {
                default: true
            }
        }
    };

</script>
