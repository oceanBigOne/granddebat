<template>
    <div class="p-1 col-12 col-sm-6 col-md-4 col-lg-3 d-flex text-left align-items-stretch">
        <span @click="onClick()" :class="getClass()">{{ tag.label }}</span>
    </div>
</template>

<script>
    export default {
        props: {
            tag: {
                type: Object,
                required: true,
            },
        },
        methods: {
            getClass() {
                return 'btn btn-block tag ' + (this.tag.checked ? 'on' : 'off') + ' ' + this.tag.color + (this.tag.is_custom ? ' italic' : '');
            },
            onClick() {
                this.$emit('tagToggled');
            },
        },
    }
</script>

<style>
    .tag {
        cursor:pointer;
       /* margin-right: 10px;
        margin-bottom: 10px;
        padding-left: 20px;
        padding-right: 20px;*/
    }

    .tag.on {
        background-color: #3490dc;
        color: #FFF;
      /*  box-shadow: inset -0.5em 0 #EAF3F9;*/
    }

    .tag.off {
       /* box-shadow: inset 0.5em 0 #FFF;*/
    }
    .tag:before{
        float: left;
        font-family:"Font Awesome 5 Free",serif;
        content: "\f111";
        font-weight:900;
        color:#fff;
    }
    .tag.on:before{
        float: left;
        font-family:"Font Awesome 5 Free",serif;
        font-weight:900;
        content: "\f058";
    }
    .tag.blue.off {
        background-color: #EAF3F9;
    }
    .tag.gray.off {
        background-color: #EEE;
    }

    .italic {
        font-style: italic;
    }

    @media (hover: hover) {
        .tag.on:hover {
            background-color: #2B76B5;
            color: #FFF;
        }

        .tag.off:hover {
            background-color: #6BAEE5;
            color: #FFF;
        }
    }
</style>