<template>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="校宝教培管理系统" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        <LoginNav />

        <div class="main">
            <div class="middle">
                <div class="left"></div>
                <div class="right">
                    <div class="loginpath">
                        <div class="phoneloginpath" @click="Phonelogin">
                            <div class="phonelogin">手机号码登录</div>
                            <div class="bluelong"></div>
                        </div>
                        <div class="schoolloginpath" @click="Schoollogin">
                            <div class="schoollogin" >机构账号登录</div>
                            <div class="bluelong"></div>
                        </div>
                    </div>
                    <div class="phone_in" v-if="showPrise">
                        <div class="phonenumber">
                            <div class="phone-icon">
                                <img class="ph-icon" src="https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1841811842,2320861044&fm=26&gp=0.jpg">
                            </div>
                            <div class="phoneblock">
                                <input class="phone" 
                                type="text" 
                                placeholder="请输入手机号" 
                                v-model="Username" 
                                :class="{borderBottom:flag[0]}" 
                                @focus="Phonefocus"
                                @blur="Phoneblur"
                                ref="Phoneinput"/>
                                <div class="pherro">
                                    <span class="herro">{{ pherromsg }}</span>
                                </div>
                            </div>
                        </div>
                        <div class="mypassword">
                            <div class="password-icon">
                                <img class="pa-icon" src="https://dss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1137786605,476002584&fm=26&gp=0.jpg"/>
                            </div>
                            <div class="passwordblock">
                                <input class="password" 
                                type="password" 
                                placeholder="请输入密码" 
                                v-model="Password"
                                :class="{borderBottom:flag[1]}" 
                                @focus="Passwordfocus"
                                @blur="Passwordblur"
                                ref="Passwordinput"/>
                                <div class="paerro">
                                    <span class="aerro" >{{ paerromsg }}</span>
                                </div>
                            </div>
                        </div>
                        <div id="loginbtn" @click="UsernameVali">
                            登录
                        </div>
                    </div>
                    <div class="school_in"  v-if="!showPrise">
                        <div class="schoolnumber">
                            <div class="schoolblock">
                                <input class="school" 
                                type="text" 
                                placeholder="请输入学校名" 
                                v-model="SchoolName" 
                                :class="{borderBottom:flag[2]}"
                                @focus="schoolnumberfocus"
                                @blur="schoolnumberblur" 
                                ref="schoolnumberinput"/>
                                <div class="scerro">
                                    <span class="serro">{{ scerromsg }}</span>
                                </div>
                            </div>
                        </div>
                        <div class="schoolpassword">
                            <div class="schoolpasswordblock">
                                <input class="schoolpa" 
                                type="password" 
                                placeholder="请输入密码" 
                                v-model="SchoolPassword"
                                :class="{borderBottom:flag[3]}" 
                                @focus="schoolpasswordfocus"
                                @blur="schoolpasswordblur"
                                ref="schoolpasswordinput"/>
                                <div class="saerro">
                                    <span class="spaerro" >{{ saerromsg }}</span>
                                </div>
                            </div>
                        </div>
                        <div class="id">
                            <div class="idblock">
                                <input class="idnumber" 
                                type="text" 
                                placeholder="请输入ID号" 
                                v-model="IdNumber" 
                                :class="{borderBottom:flag[4]}"
                                @focus="idnumberfocus" 
                                @blur="idnumberblur"
                                ref="idnumberinput"/>
                                <div class="iderro">
                                    <span class="ierro">{{ iderromsg }}</span>
                                </div>
                            </div>
                        </div>
                        <div id="Schoolloginbtn" @click="SchoolVali">
                            登录
                        </div>
                    </div>
                </div>
            </div>

            <div class="footer">
                <div class="product"> 
                    <div class="xiangguan">相关产品</div>
                    <div class="smallproduct">
                        <div class="scp">
                            <div class="scpicon">
                                <img class="scp-icon" src="https://prox.schoolpal.cn/common/images/icon-scp.png"/>
                                <div class="scptext">
                                    <div class="scpname">校宝收银宝</div>
                                    <div class="scpintr">学校收费标配</div>
                                </div>
                            </div>
                        </div>
                        <div class="zhaoshengbao">
                            <div class="zhaoshengbaoicon">
                                <img class="zhaosheng-icon" src="https://prox.schoolpal.cn/common/images/icon-zhaoshengbao.png"/>
                                <div class="zhaoshengbaotext">
                                    <div class="zhaoshengname">校宝招生宝</div>
                                    <div class="zhaoshengintr">一站招生服务</div>
                                </div>
                            </div>
                        </div>
                        <div class="anxinbao">
                            <div class="anxinbaoicon">
                                <img class="anxin-icon" src="https://prox.schoolpal.cn/common/images/icon-anxinbao.png"/>
                                <div class="anxinbaotext">
                                    <div class="anxinname">校宝安心宝</div>
                                    <div class="anxinintr">教育保险精选</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="hotline">
                    <div class="hotlinetext">
                        咨询热线
                    </div>
                    <div class="hotlinenumber">
                        400-699-707
                    </div>
                </div>
            </div>
        </div>
    </body>
    </html>
</template>


<script>
    import LoginNav from '@/components/LoginNav'

    export default {
        name: 'Login',
        components: {
            'LoginNav' : LoginNav
        },
        data(){
            return{
                phonelogin:0,
                Username: '',
                Password: '',
                pherromsg: '',
                paerromsg: '',
                SchoolName: '',
                SchoolPassword: '',
                IdNumber: '',
                iderromsg: '',
                saerromsg: '',
                scerromsg: '',
                showPrise:true,
                flag:[false,false,false,false,false]
            }
        },
        methods:{  
            Phonefocus:function(){
                this.$refs.Phoneinput.style.borderBottom="1px solid #007AFF";
            },
            Phoneblur:function(){
                this.$refs.Phoneinput.style.borderBottom="1px solid #f0f0f0";
            },
            Passwordfocus:function(){
                this.$refs.Passwordinput.style.borderBottom="1px solid #007AFF";
            },
            Passwordblur:function(){
                this.$refs.Passwordinput.style.borderBottom="1px solid #f0f0f0";
            },
            schoolnumberfocus:function(){
                this.$refs.schoolnumberinput.style.borderBottom="1px solid #007AFF";
            },
            schoolnumberblur:function(){
                this.$refs.schoolnumberinput.style.borderBottom="1px solid #f0f0f0";
            },
            schoolpasswordfocus:function(){
                this.$refs.schoolpasswordinput.style.borderBottom="1px solid #007AFF";
            },
            schoolpasswordblur:function(){
                this.$refs.schoolpasswordinput.style.borderBottom="1px solid #f0f0f0";
            },
            idnumberfocus:function(){
                this.$refs.idnumberinput.style.borderBottom="1px solid #007AFF";
            },
            idnumberblur:function(){
                this.$refs.idnumberinput.style.borderBottom="1px solid #f0f0f0";
            },
            UsernameVali:function(){
                if(this.Username.length!=11&&this.Username.length!=0){
                    this.pherromsg="请输入正确的手机号码";
                    this.paerromsg="";
                    this.flag[0]=true;
                    this.flag[1]=false;
                }else if((this.Password===""||this.Password===null)&&(this.Username===""||this.Username===null)){
                    this.pherromsg="请输入手机号码";
                    this.paerromsg="请输入密码";
                    this.flag[0]=true;
                    this.flag[1]=true;
                }else if((this.Username===""||this.Username===null)&&(this.Password!=""||this.Password!=null)){
                    this.pherromsg="请输入手机号码";
                    this.paerromsg="";
                    this.flag[0]=true;
                    this.flag[1]=false;
                }else if((this.Password===""||this.Password===null)&&(this.Username!=""||this.Username!=null)){
                    this.paerromsg="请输入密码";
                    this.pherromsg="";
                    this.flag[0]=false;
                    this.flag[1]=true;
                }
            },
            SchoolVali:function(){
                if(this.SchoolName===""&&this.SchoolPassword===""&&this.IdNumber==""){
                    this.scerromsg="请填写完整学校名";
                    this.saerromsg="请填写密码";
                    this.iderromsg="请填写学校id";
                    this.flag[2]=true;
                    this.flag[3]=true;
                    this.flag[4]=true;
                }
            },
            
            Phonelogin:function(){
                this.showPrise = true;
            },
            Schoollogin:function(){
                this.showPrise = false;
            }
        }
    }


   
</script>


<style>
    .loginpath{
        display: flex;
        justify-content: space-between;
        flex-direction: row;
        width: 60%;
    }

    .borderBottom{
        border-bottom: 1px solid #ff3366 !important;
    }

    html,body{
        margin: 0;
        height: 100%;
    }

    .main{
        height: 877px;
        display: flex;
        background-color: #F2F6FC;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .middle{
        display: flex;
        justify-content: space-between;
        width: 1000px;
        height: 510px;
        margin: 0 auto;
        border-radius: 8px;
        background-color: white;
    }

    .middle .left{
        display: block;
        width: 560px;
        height: 510px;
        overflow: hidden;
        background-image: url(https://schoolpal.oss-cn-hangzhou.aliyuncs.com/erpbanner/erplogin0827.jpg);
        background-repeat: no-repeat;
        background-size: 560px 510px;
    }

    .middle .right{
        display: flex;
        width: 440px;
        flex-direction: column;
        align-items: center;
        position: relative;
    }

    .middle .right .phonelogin{
        display: block;
        padding-top: 80px;
        font-size: 18px;
        font-weight: bold;
    }

    .middle .right .schoollogin{
        display: block;
        padding-top: 80px;
        font-size: 18px;
        font-weight: bold;
    }

    .middle .right .bluelong{
        display: block;
        width: 32px;
        height: 5px;
        border-radius: 4px;
        background-color: #007AFF;
        margin-top: 10px;
        margin-left: 40px;
    }

    .phone-icon, .password-icon{
        display: flex;
        align-items: center;
    }

    .middle .right .phonenumber{
        display: flex;
        width: 340px;
        margin-top: 40px;
        margin-bottom: 25px;
        visibility: visible;
    }

    .middle .right .mypassword{
        display: flex;
        width: 340px;
        margin-top: 25px;
        visibility: visible;
    }

    .ph-icon, .pa-icon{
        margin-right: 20px;
        width: 12px;
        height: 12px;
        margin-bottom: 20px;
    }

    .phonenblock, .passwordblock{
        display: flex;
        flex-direction: column;
    } 

    .middle .right .schoolnumber, .schoolpassword, .id{
        display: flex;
        width: 340px;
        margin-top: 40px;
        margin-bottom: 25px;
        visibility: visible;
    }

    .phone, .password, .school, .schoolpa, .idnumber{
        border: 0;  
        outline: none; 
        background-color: rgba(0, 0, 0, 0);
        padding-bottom: 10px;
        font-size: 14px;
        display: block;
        width: 320px;
        border-bottom: 1px solid #f0f0f0;
    }

    .pherro, .paerro{
        display: flex;
        flex-direction: row-reverse;
        width: 100%;
        line-height: 100%;
    }

    .herro, .aerro{
        font-size: 12px;
        color:#f34;
        padding-right: 20px;
        display: block;
    }

    #loginbtn{
        width: 320px;
        height: 54px;
        font-size: 16px;
        background-color: #007AFF;
        font-weight: bold;
        color:white;
        text-align: center;
        border-radius: 50px;
        line-height: 54px;
        margin: 0 auto;
        position: absolute;
        bottom: 30px;
        visibility: visible;
    }

    #Schoolloginbtn{
        width: 320px;
        height: 54px;
        font-size: 16px;
        background-color: #007AFF;
        font-weight: bold;
        color:white;
        text-align: center;
        border-radius: 50px;
        line-height: 54px;
        margin: 0 auto;
        position: absolute;
        bottom: 30px;
        visibility: visible;
    }

    .footer{
        display: flex;
        width: 1000px;
        flex-direction: row;
        margin: 0 auto;
        justify-content: space-between;
    }

    .product, .hotline{
        display: flex;
        flex-direction: column;
        padding-top: 10px;
    }

    .smallproduct{
        display: flex;
        flex-direction: row;
    }

    .xiangguan, .hotlinetext{
        font-size: 16px;
        font-weight: bold;
    }

    .scp, .zhaoshengbao, .anxinbao{
        width: 210px;
        height: 60px;
        margin-right: 10px;
        border-radius: 8px;
        display: flex;
        flex-direction: row;
        justify-content: center;
        margin: 0 auto;
    }

    .scp-icon, .zhaosheng-icon, .anxin-icon{
        width: 30px;
        height: 30px;
        margin-right:10px ;
    }

    .scpicon, .zhaoshengbaoicon, .anxinbaoicon{
        display: flex;
        flex-direction: row;
        justify-content: center;
        padding: 10px;
    }

    .scpname, .zhaoshengname, .anxinname{
        font-size: 14px;
        font-weight: bold;
        justify-content: center;
    }

    .scpintr, .zhaoshengintr, .anxinintr{
        font-size: 12px;
        justify-content: center;
    }

    .hotline{
        margin-right: 10px;
    }

    .hotlinenumber{
        font-size: 28px;
        font-weight: bold;
        margin-top: 22px;
    }

    #loginbtn:hover{
        background-color:#0064dc;
        cursor:pointer;
    }

    /* .password:focus, .phone:focus{
        border-bottom: 1px solid #007AFF;
    } */

    .scp:hover, .zhaoshengbao:hover, .anxinbao:hover{
    background-color: rgba(245, 203, 207, 1);
    cursor:pointer;
    }
</style>
