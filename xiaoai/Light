/**********************************************************
*    文件: ESP32_Blinker_Light.ino      by 零知实验室(www.lingzhilab.com)
*    -^^- 零知开源，让电子制作变得更简单！ -^^-
*    时间: 2020/01/05 19:24
*    说明:
************************************************************/
#define BLINKER_WIFI
#define BLINKER_MIOT_LIGHT

#include <Blinker.h>

char auth[] = "xxxxxxxxx";
char ssid[] = "TP-LINK_4CDF";
char pswd[] = "xxxxxxx";

int pumpin = 16;//续电器引脚 低电平触发

void miotPowerState(const String & state)
{
	BLINKER_LOG("need set power state: ", state);
	
	if (state == BLINKER_CMD_ON) {
		BLINKER_LOG("小爱开启指令", state);
		digitalWrite(pumpin,LOW);//打开
		
		BlinkerMIOT.powerState("on");
		BlinkerMIOT.print();
		
	}
	else if (state == BLINKER_CMD_OFF) {
		BLINKER_LOG("小爱关闭指令", state);
		
		digitalWrite(pumpin,HIGH);
		BlinkerMIOT.powerState("off");
		BlinkerMIOT.print();
		
	}
}

// 复位或上电后运行一次:
void setup() {
	//在这里加入初始化相关代码，只运行一次:
	
	Serial.begin(115200);
	BLINKER_DEBUG.stream(Serial);
	
	// 初始化继电器IO
	pinMode(pumpin,OUTPUT);
	digitalWrite(pumpin,HIGH);
	Blinker.begin(auth, ssid, pswd);
	//小爱回调函数
	BlinkerMIOT.attachPowerState(miotPowerState);
	
}

//一直循环执行:
void loop() {
	// 在这里加入主要程序代码，重复执行:
	Blinker.run();
}
