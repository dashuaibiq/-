# -
魔方18电信3班 刘岗
（文档）。准备就绪（函数
//定义各个位置电机的控制信号的针脚（PUL->脉冲信号，DIR->转向信号）：

int U_PUL = 22 ;
int U_DIR = 23 ;

int R_PUL = 24 ;
int R_DIR = 25 ;

int F_PUL = 26 ;
int F_DIR = 27 ;

int D_PUL = 28 ;
int D_DIR = 29 ;

int L_PUL = 30 ;
int L_DIR = 31 ;

int B_PUL = 32 ;
int B_DIR = 33 ;

//还原状态（0为未还原，1为已还原，初始化为0）
int IS_OK = 0 ;

//魔方解法
char  const * solve [ 22 ] = { “ U ”，“ D' ”，“ L ”，“ U' ”，“ L2 ”，“ D' ”，“ R2 ”，“ F ”，“ U2 ”，“ B ' “，” U' “，” L' “，“ B2 ”，“D ”，“ L2 ”，“ D ”，“ R2 ”，“ B2 ”，“ L2 ”，“ D' ”，“ R2 ”，“ U2 ” }；

无效 设置（）
{
    //初始化针脚
    pinMode（U_PUL，OUTPUT）;
    pinMode（U_DIR，OUTPUT）;

    pinMode（R_PUL，OUTPUT）;
    pinMode（R_DIR，OUTPUT）;

    pinMode（F_PUL，OUTPUT）;
    pinMode（F_DIR，OUTPUT）;

    pinMode（D_PUL，OUTPUT）;
    pinMode（D_DIR，OUTPUT）;

    pinMode（L_PUL，OUTPUT）;
    pinMode（L_DIR，OUTPUT）;

    pinMode（B_PUL，OUTPUT）;
    pinMode（B_DIR，OUTPUT）;
}

无效 循环（）
{
    如果（IS_OK == 0）
    {
        对于（int i = 0 ; i < 22 ; i ++）
        {
            //上
            if（strcmp（“ U ”，resolve [i]）== 0）
            {
                移动（1，0，U_PUL，U_DIR）;
            }
            否则 if（strcmp（“ U' ”，resolve [i]）== 0）
            {
                移动（0，0，U_PUL，U_DIR）;
            }
            否则 if（strcmp（“ U2 ”，resolve [i]）== 0）
            {
                移动（1，1，U_PUL，U_DIR）;
            }

            //右
            否则 if（strcmp（“ R ”，resolve [i]）== 0）
            {
                移动（1，0，R_PUL，R_DIR）;
            }
            否则 if（strcmp（“ R' ”，resolve [i]）== 0）
            {
                移动（0，0，R_PUL，R_DIR）;
            }
            否则 if（strcmp（“ R2 ”，resolve [i]）== 0）
            {
                移动（1，1，R_PUL，R_DIR）;
            }

            //前
            否则 if（strcmp（“ F ”，resolve [i]）== 0）
            {
                移动（1，0，F_PUL，F_DIR）;
            }
            否则 if（strcmp（“ F' ”，resolve [i]）== 0）
            {
                移动（0，0，F_PUL，F_DIR）;
            }
            否则 if（strcmp（“ F2 ”，resolve [i]）== 0）
            {
                移动（1，1，F_PUL，F_DIR）;
            }

            //下
            否则 if（strcmp（“ D ”，resolve [i]）== 0）
            {
                移动（1，0，D_PUL，D_DIR）;
            }
            否则 if（strcmp（“ D' ”，resolve [i]）== 0）
            {
                移动（0，0，D_PUL，D_DIR）;
            }
            否则 if（strcmp（“ D2 ”，resolve [i]）== 0）
            {
                移动（1，1，D_PUL，D_DIR）;
            }

            //左
            否则 if（strcmp（“ L ”，resolve [i]）== 0）
            {
                移动（1，0，L_PUL，L_DIR）;
            }
            否则 if（strcmp（“ L' ”，resolve [i]）== 0）
            {
                移动（0，0，L_PUL，L_DIR）;
            }
            否则 if（strcmp（“ L2 ”，resolve [i]）== 0）
            {
                移动（1，1，L_PUL，L_DIR）;
            }

            //后
            否则 if（strcmp（“ B ”，resolve [i]）== 0）
            {
                移动（1，0，B_PUL，B_DIR）;
            }
            否则 if（strcmp（“ B' ”，resolve [i]）== 0）
            {
                移动（0，0，B_PUL，B_DIR）;
            }
            否则 if（strcmp（“ B2 ”，resolve [i]）== 0）
            {
                移动（1，1，B_PUL，B_DIR）;
            }
        }

        IS_OK = 1；
    }
}

/ 
    int pul_count = 0 ;

    //根据状态码判断当前输入的转动方向
    如果（d_status == 0）
    {
        digitalWrite（DIR，LOW）; //前进电机顺时针转动，魔方逆时针转动
    }
    否则 ，如果（d_status == 1）
    {
        digitalWrite（DIR，HIGH）; //高功率电机逆时针转动，魔方顺时针转动
    }

    //将转动角度信号转化为对应角度的脉冲
    如果（a_status == 0）
    {
        pul_count = 200 ;
    }
    否则 ，如果（a_status == 1）
    {
        pul_count = 400 ;
    }

    //转动电机
    为（int i = 0 ; i <pul_count; i ++）
    {
        digitalWrite（PUL，HIGH）;
        delayMicroseconds（400）;
        digitalWrite（PUL，LOW）;
    }
    //   delay（1）;
} 
