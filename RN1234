#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "Ravi";
const char* password = "raviraj12";
ESP8266WebServer server(80);

String page ="";
int data ;
void setup(void)
{
  pinMode(A0,INPUT);

  delay(1000);
  Serial.begin(115200);
  WiFi.begin(ssid, password);
  Serial.println("");
  pinMode(D0, OUTPUT);
  while (WiFi.status() != WL_CONNECTED)
  {
  delay(500);
  Serial.print(".");
  
  }
  Serial.println("");
  Serial.print("Connected to");
  Serial.println(ssid);
  Serial.print("IP address: ");
  Serial.print(WiFi.localIP());
  server.on("/",[](){
    page = "<h1>Sensor to node MCU Web Server</h1><h3>Data:</h3><h4>" + String(data)+"</h4>";
    server.send(200,"text/html",page);
    
    
  });
  server.begin();
  Serial.println("Web server started !");
  
}

void loop(void)
{
  float data1 = analogRead(A0);
  data=100-((data1/1024)*100);
  if (data>=70)
  {
  Serial.println("soil is good,no water needed");
  }
  else
  {
  Serial.println("Need to water");
  }
  delay(1000);
  server.handleClient();
}
