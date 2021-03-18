<template>
    <div >
        <div style="background: #ebebeb;height: 50px;border-radius: 30px;padding: 5px 10px;overflow: hidden;">
            <div style="float: left;display: block;">
            <span>  <img :src="comment.avatar" alt="" style="width: 40px;height: 40px;border-radius: 100%;align-self: start;"></span>
            </div>
            <div style="padding-top: 15px;text-align: left;margin-left: 5px;">
                <span style="margin-left:10px">{{ comment.text }}</span>
            </div>
        </div>
        <div style="width: auto;text-align: left;margin-left: 40px;">
            <button class="rply"  v-on:click="isHidden = false" style="border:none; background:none" ><i class="fa fa-paper-plane"></i> Reply</button>
        </div>
        <div v-if="!isHidden">
            <div style="background: rgb(235, 235, 235); height: 50px; border-radius: 30px; padding: 5px 10px; overflow: hidden;
                    margin-left: 20px;margin-top: 5px;">
                    <div style="float: left; display: block;">
                    <span>  <img :src="comment.avatar" alt="" style="width: 40px;  height: 40px; border-radius: 100%; align-self: start;"></span>
                    </div>
                     <div class="reply">
                            <div style="padding-top: 10px; text-align: left; margin-left: 5px;">
                                <input style="border: 0px;
                                    color: rgb(51, 51, 51);
                                    outline: 0px;
                                    background-color: transparent;
                                    box-shadow: none;
                                    width: fit-content;
                                    min-height: 0px;
                                    padding: 0px;
                                    margin-right: 0px;"
                                type="text" 
                                v-model.trim="reply1" 
                                class="reply--text" 
                                placeholder="Leave a comment..."
                                maxlength="250"
                                required
                                @keyup.enter="submitReply1"
                                />
                            <button class="reply--button" @click.prevent="submitReply1" style="top: 2px;"><i class="fa fa-paper-plane"></i> Send</button>
                        </div> 
                    </div>
                </div> 
                <div style="width: auto;text-align: left;margin-left: 40px;">
                <button class="rply"  v-on:click="isHidden2 = false" style="border:none; background:none" ><i class="fa fa-paper-plane"></i> Reply</button>
            </div>
        </div>   

        <div v-if="!isHidden2">
            <div style="background: rgb(235, 235, 235); height: 50px; border-radius: 30px; padding: 5px 10px; overflow: hidden;
                    margin-left: 35px;margin-top: 5px;">
                    <div style="float: left; display: block;">
                    <span>  <img :src="comment.avatar" alt="" style="width: 40px;  height: 40px; border-radius: 100%; align-self: start;"></span>
                    </div>
                     <div class="reply">
                            <div style="padding-top: 10px; text-align: left; margin-left: 5px;">
                                <input style="border: 0px;
                                    color: rgb(51, 51, 51);
                                    outline: 0px;
                                    background-color: transparent;
                                    box-shadow: none;
                                    width: fit-content;
                                    min-height: 0px;
                                    padding: 0px;
                                    margin-right: 0px;"
                                type="text" 
                                v-model.trim="reply2" 
                                class="reply--text" 
                                placeholder="Leave a comment..."
                                maxlength="250"
                                required
                                @keyup.enter="submitReply2"
                                />
                            <button class="reply--button" @click.prevent="submitReply2" style="top: 2px;"><i class="fa fa-paper-plane"></i> Send</button>
                            </div> 
                    </div>
                </div> 
                <div style="width: auto;text-align: left;margin-left: 40px;">
                <button class="rply"  v-on:click="isHidden3 = false" style="border:none; background:none" ><i class="fa fa-paper-plane"></i> Reply</button>
            </div>
        </div>  
        <div v-if="!isHidden3">
                <div style="background: rgb(235, 235, 235); height: 50px; border-radius: 30px; padding: 5px 10px; overflow: hidden;
                    margin-left: 45px;margin-top: 5px;">
                    <div style="float: left; display: block;">
                    <span>  <img :src="comment.avatar" alt="" style="width: 40px;  height: 40px; border-radius: 100%; align-self: start;"></span>
                    </div>
                        <div class="reply">
                            <div style="padding-top: 10px; text-align: left; margin-left: 5px;">
                                <input style="border: 0px;
                                    color: rgb(51, 51, 51);
                                    outline: 0px;
                                    background-color: transparent;
                                    box-shadow: none;
                                    width: fit-content;
                                    min-height: 0px;
                                    padding: 0px;
                                    margin-right: 0px;"
                                type="text" 
                                v-model.trim="reply3" 
                                class="reply--text" 
                                placeholder="Leave a comment..."
                                maxlength="250"
                                required
                                @keyup.enter="submitReply3"
                                />
                            <button class="reply--button" @click.prevent="submitReply3" style="top: 2px;"><i class="fa fa-paper-plane"></i> Send</button>
                            </div> 
                        </div>
                    </div> 
                <div style="width: auto;text-align: left;margin-left: 40px;">
                <button class="rply"  v-on:click="isHidden3 = false" style="border:none; background:none" ><i class="fa fa-paper-plane"></i> Reply</button>
            </div> 
        </div>  
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: 'singleComment',
        data() {
            return {
                reply: '',
                reply1: '',
                reply2: '',
                reply3: '',
                isHidden: true,
                isHidden2: true,
                isHidden3: true
            }
                        },
        props: ['comment'],
        methods: {
            submitReply1() {
                var temp = {"Comment":this.reply1}
                axios.post("http://127.0.0.1:8000/api/saveComments", temp)
                .then(response => console.log(response))
                .catch(error => {
                this.errorMessage = error.message;
                console.error("There was an error!", error);
                });
            },
            submitReply2() {
                var temp = {"Comment":this.reply2}
                axios.post("http://127.0.0.1:8000/api/saveComments", temp)
                .then(response => console.log(response))
                .catch(error => {
                this.errorMessage = error.message;
                console.error("There was an error!", error);
                });
            },
            submitReply3() {
                var temp = {"Comment":this.reply3}
                axios.post("http://127.0.0.1:8000/api/saveComments", temp)
                .then(response => console.log(response))
                .catch(error => {
                this.errorMessage = error.message;
                console.error("There was an error!", error);
                });
            },
        }
    }
</script>

<style scoped>
/* Single-comment component */
.comment {
    display: flex;
    padding: 10px;
    margin-bottom: 10px;
    align-items: center;
    color: #333;
    background-color: #F2F2F2;
    border-radius: 30px;
    box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
}
.rply{
    border:none;
    background: none;
}
.rply:active{
    border:none;
}
.comment .avatar {
    align-self: flex-start;
}
.comment .avatar > img {
    width: 40px;
    height: 40px;
    border-radius: 100%;
    align-self: start;
}
.comment .text {
    text-align: left;
    margin-left: 5px;
}
.comment .text span {
    margin-left: 5px;
}
.comment .text .username {
    font-weight: bold;
    color: #333;
}
button :hover{
    border: none !important;
}
button :active{
    border: none  !important;
}
button :focus{
    border: none;
}
.commentChild {
    display: flex;
    padding: 10px;
    margin-bottom: 10px;
    align-items: center;
    color: #333;
    background-color: #F2F2F2;
    border-radius: 30px;
    box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
}
.commentChild .avatar {
    align-self: flex-start;
}
.commentChild .avatar > img {
    width: 40px;
    height: 40px;
    border-radius: 100%;
    align-self: start;
}
.commentChild .text {
    text-align: left;
    margin-left: 5px;
}
.comment .text span {
    margin-left: 5px;
}
.commentChild .text .username {
    font-weight: bold;
    color: #333;
}


.reply {
    display: flex;
    position: relative;
    align-items: center;
    background-color: #EBEBEB;
    border-radius: 30px;
    padding: 5px 10px;
    overflow: hidden;
}
.reply .avatar {
    position: absolute;
}
.reply .avatar > img {
    width: 40px;
    height: 40px;
    border-radius: 100%;
}
.reply .reply--text {
    min-height: 40px;
    padding: 10px 10px 10px 55px;
    margin-right: 10px;
    border: 0;
    color: #333;
    width: 100%;
    outline: 0;
    background-color: transparent;
    box-shadow: none;
}
.reply input.reply--text:valid {
    margin-right: 71px;
}
.reply input.reply--text:valid + .reply--button {
    right: 10px;
}
.reply .reply--button {
    position: absolute;
    right: -100px;
    border: 1px solid #2a629c;
    background-color: transparent;
    color: #2a629c;
    display: inline-block;
    font-weight: 400;
    text-align: center;
    white-space: nowrap;
    vertical-align: middle;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    padding: 0.375rem 0.75rem;
    font-size: 15px;
    line-height: 1.5;
    border-radius: 30px;
    transition: color 0.25s ease-in-out, background-color 0.25s ease-in-out, border-color 0.25s ease-in-out, box-shadow 0.25s ease-in-out, right 0.25s ease-in-out;
    outline: 0;
}
.reply .reply--button:hover {
    color: #fff;
    background-color: #2a629c;
}
.reply .reply--button:focus,
.reply .reply--button:active {
    box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
}
hr {
    margin-top: 10px;
    margin-bottom: 10px;
}

</style>