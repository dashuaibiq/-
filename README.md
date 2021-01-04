一八电信三班刘岗
void turn()               //转魔方
{
	void computer();
	void coloring();
	char turn[100] = "";
	bool ifwin();
	int word(char word[]);
 
	system("color BD");  //设置控制台前景色和背景色
 
	for(int i = 0; i<100; i++)
	{
		turn[i] = '1';
	}
	i = 0;
 
	turn[i] = getch();   //不能用getchar();不然每次都要输入回车
	cout<<endl<<"你的步骤如下:"<<endl;
	cout<<turn[i]<<" ";
	while(turn[i]!='0')
	{
		switch(turn[i])
		{
			case'R':Right();break;
			case'r':right();break;
			case'U':Up();break;
			case'u':up();break;
			case'L':Left();break;
			case'l':left();break;
			case'D':Down();break;
			case'd':down();break;
			case'F':Front();break;
			case'f':front();break;
			case'B':Back();break;
			case'b':back();break;
			case'M':M();break;
			case'm':m();break;
			case'X':X();break;
			case'x':x();break;
			case'Y':Y();break;
			case'y':y();break;
			case'Z':Z();break;
			case'z':z();break;
			case'+':computer();break;  //电脑控制(层先法)
	//		case'*':break;    //电脑控制(逆序法)
			case'0':exit(1);
			default:break;             //不能是continue;不然输入其他键,图形无变化,但也会显示win
		}
 
		if(ifwin())        //判断是否复原
		{
			word("Congratulations!You win~(碰我重新开始哦^_^)");
			for(i = 0; i<100; i++)    //重新开始，再次初始化
			{
				turn[i] = '1';
			}
			i = 0;
			cout<<endl<<"你的步骤如下:"<<endl;
	//		turn[i] = getch();   //不能在这儿输入，不然会漏一个
	//		cout<<turn[i]<<" ";
		}
 
		if(turn[i]=='*'||turn[i+1]!='1')   //按下‘*’后用逆序步骤的方法复原
		{
			if(turn[i]=='*')
			{
				cout<<endl<<"电脑逆序复原步骤如下:"<<endl;
			}
			i--;
			if(65<=turn[i]&&turn[i]<=90)
			{
				turn[i] = turn[i] + 32;
			}
			else if(97<=turn[i]&&turn[i]<=122)
			{
				turn[i] = turn[i] - 32;
			}
			cout<<turn[i]<<" ";
			Sleep(1000);
		}
		else         //没按‘*’或‘+’则继续输入，手工旋转魔方
		{
			i++;
			turn[i] = getch();	
			cout<<turn[i]<<" ";
		}
	}
