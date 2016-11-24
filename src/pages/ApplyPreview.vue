<style scoped lang="stylus" rel="stylesheet/stylus">
    .apply
        overflow hidden
        .meter
            position relative
            overflow hidden
            &.step1
                .progress
                    border-right-width 705px
                    border-left-width 475px
            &.step2
                .progress
                    border-right-width 471px
                    border-left-width 709px
            &.step3
                .progress
                    border-right-width 0
                    border-left-width 1180px
            .progress
                position absolute
                top 89px
                height 2px
                border-style none solid
                border-right-color rgb(188, 188, 188)
                border-left-color black
            .circle
                position relative
                float left
                margin-top 70px
                width 36px
                height @width
                border-width 2px
                border-style solid
                border-radius 50%
                text-align center
                line-height 34px
                z-index 1
                &.normal
                    background-color white
                    border-color rgb(188, 188, 188)
                &.done
                    background-color black
                    border-color @background-color
                    color white
                &:before
                    position absolute
                    top -44px
                    left ((@width + @border-width * 2) / 2)
                    font-size 15px
                    white-space nowrap
                    color black
                    transform translateX(-50%)
                &:nth-of-type(1)
                    margin-left 338px
                    &:before
                        content "描述您的需求"
                &:nth-of-type(2)
                    margin-left 194px
                    &:before
                        content "预览您的需求"
                &:nth-of-type(3)
                    margin-left 194px
                    &:before
                        content "发送需求成功"
        form
            float left
            margin-top 30px
            padding 26px
            width 872px
            height 723px
            border 1px solid rgb(242,242,242)
            font-size 14px
            position relative
            .form_1
                overflow hidden
                span
                    &:first-child
                        float left
                    &:last-child
                        float right
            p
                margin-top 25px
                &:last-of-type
                    width 650px
            .form_2
                height 250px
                margin-top 100px
                i
                    height @height
                    width @height
                    margin-right 15px
                    background-size contain
                    background-repeat no-repeat
                    display inline-block
                    border-radius 50%

            .form_3
                position absolute
                bottom 30px
                a
                    width 100px
                    height 30px
                    border-radius 5px
                    background rgb(166,166,166)
                    display inline-block
                    text-align center
                    line-height @height
                    color white
                    margin-right 15px


    body
        width 100%
</style>
<template>
    <div class="apply w1180">
        <div class="meter step2">
            <div class="circle done">1</div>
            <div class="circle done">2</div>
            <div class="circle normal">3</div>
            <div class="progress"></div>
        </div>
        <form>
            <div class="form_1">
                <span v-text="req"></span>
                <span>申请类目:{{type}}</span>
            </div>
            <p>联系电话:{{tel}}</p>
            <p>申请具体要求:</p>
            <p>{{detail}}</p>
            <div class="form_2">
                <i :style="{'background-image': 'url(' + path + ')'}" alt=""></i>
                <i :style="{'background-image': 'url(' + path + ')'}" alt=""></i>
                <i :style="{'background-image': 'url(' + path + ')'}" alt=""></i>


            </div>
            <div class="form_3">
                <router-link :to="'/applyStart'">修改需求</router-link>
                <router-link :to="href" @handleClick>发布需求</router-link>
            </div>
        </form>
        <apply-right></apply-right>
    </div>

</template>
<script>
    import ApplyRight from '../components/ApplyRight.vue'
    export default{
        methods:{
            handleClick(){

            }
        },
        created(){
            console.log(this.$router)
        },
        data(){
            const {
                req,
                type,
                tel,
                detail,
                path
            } = this.$route.query;
            return{
                href: '/applyPost',
                req,
                type,
                tel,
                detail,
                path
            }
        },
        components:{
            ApplyRight
        }
    }
</script>
