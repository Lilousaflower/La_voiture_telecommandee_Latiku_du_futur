# Robot Télécommandé - *Lakitu du Futur* 
Documentation pour vous permettre de construire un robot télécommandé **Lakitu du Futur**.
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_final_1.png?raw=true">

## Matériel Nécessaire 
- Maya 2024
- Imprimante 3D
- Papier aluminimum
- Peinture Jaune, Marron et Argenté
- Fil de Fer
- Pistolet à Colle
- Bois fin ou carton épais
- Boules de coton

Pour le moteur :
- NodeMCU Esp8266
- Cd 4066
- Moteur driver
- 2 moteurs
- 1 pile 9V
- Interrupteur
- Limiteur de courant
- Joystick
- Fils électriques
  
## Sommaire de Création
1. Création 3D de la coque
      - Récupération d'un modèle
      - Modification du modèle
      - Export des fichiers
      - Impression 3D
2. Montage du moteur et des roues
3. Codage
      - La voiture
      - Le joystick
3. Assemblage et Personnalisation de la coque
      - Création des accessoires
      - Peinture
      - Assemblage des élements 

## 1. Création 3D de la coque 
La première étape consiste à imaginer et créer la coque de notre robot. 
D'abord, il faut récupérer un modèle 3D sur internet qui convient au niveau de la forme globale au résultat attendu pour notre robot : [Lien vers le modèle](https://cults3d.com/fr/mod%C3%A8le-3d/jeu/lakitu-from-mario-games-multi-color).

Puis, il faut réparer et réadappter un peu le modèle selon nos besoins. Pour ça nous allons utiliser _**Maya**_ qui va nous permettre de retopo le modèle, et _**Blender**_ pour les modifications des élements, Blender étant un logiciel plus accessible et facile à prendre en main. Il est possible d'utiliser uniquement Maya.  

- D'abord, nous importons et reconstituons le modèle téléchargé depuis Internet, et nous gardons uniquement les élements qui nous intéressent, à savoir le nuage, le corps, la tête, les bras et la carapace. Il faut bien faire attention à ce que le modèle soit à la bonne échelle (à savoir 10cm de large) :
  
Reconstitution du modèle | Eléments intéressants
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_og.png?raw=true" width="500">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_v2.png?raw=true" width="509.7">

- Puis, nous allons cleaner et reboucher les trous présents dans les mesh. Exemple avec le nuage, on retire les polygones en trop dans les trous, et on rebouche ceux-ci grâce à un *"Fill"*, puis on lisse grossièrement les reliefs en mode sculpt grâce au bruch *"Smooth"*. Il faut faire ça aussi avec le corps (où on va retirer la partie basse qui servait de support, et reboucher les bras), et la tête (on rebouche les yeux et le trous au dessus de son crâne). Petite spécificité au nuage : nous voulons laisser l'intérieur creux pour l'impression 3D, afin d'y glisser les LED par la suite
  
Avant | Après
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_old.png?raw=true" width="450">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_new.png?raw=true" width="540">

- Pour le bras droit, nous allons tout simplement suprimmer la main, et la remplacer par la main gauche du modèle que nous aurons copié, mis en symétrie, et rattaché au reste du bras droit :

Avant | Après
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/bras_avant%20.png?raw=true" width="445">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/bras_apres.png?raw=true" width="470">

- Puis, nous allons recréer des petits élements, à savoir les yeux et la bouche du nuage (avec des demi-sphères qu'on met à la bonne taille), ainsi que la carapace (qui est aussi une demi sphère) : 

Visage | Carapace
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/nuage_visage.png?raw=true" width="500">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/carapace.png?raw=true" width="400">

- Enfin, nous allons regouper tous nos élements en un seul mesh gâce à des boolean :
    - Un premier boolean sur le nuage, en mode *"Union"*, dans lequel on rattache les yeux et la bouche.
    - Un deuxième boolean sur le corps, en mode *"Union"*, dans lequel on rattache les bras.
    - Un dernier boolean sur le corps, en mode *"Union"*, dans lequel on rattache la carapace.
      
 Ainsi, une fois tous les boolean Apply, nous nous retrouvons avec 2 meshs distincts : 1 pour la tête et 1 pour tout le reste des élements. Nous allons exporter ces 2 meshs en 2 fbx pour les passer sur Maya.

 Une fois Maya 2024 ouvert, nous allons commencer par importer la tête. Une fois le mesh importer, il suffit de le sélectionner, et de cliquer dans le menu Mesh > Retopologize > carré d'options. Le seul paramètre que nous allons modifier est le *"Target Face Count"* que nous allons mettre à 25000. Celà correspond au nombre de polygones. Plus il y a de polygones, plus on garde les détails. Enfin, il faut cliquer sur "Retopologize", et votre mesh à désormais un maillage uniforme ! Nous allons procéder exactement de la même manière pour le corps, en y mettant 50000 polygones. 

 Tête | Corps
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/t%C3%AAte_retopo.png?raw=true" width="485">  |  <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/corps_retopo.png?raw=true" width="470">

Enfin, nous avons modéliser sur Blender des roues de diamètre 6cm et largeur 1.5cm.  
Lorsque vous avez terminé vos modélisations et retopo, il vous suffit d'exporter vos fichiers en stl, et ils sont désormais prêts à être importés dans votre logiciel d'imprimante 3D ! Nous imprimerons uniquement avec du filament blanc.

## 2. Montage du moteur et des roues
Il est temps de passer au montage du moteur qui va nous permettre de faire tourner les roues, et de pouvoir les contrôler grâce à un joystick (les cartes ESP8266 nous permettent de communiquer ensemble et donc la voiture devient pilotable sans fils). Nous avons aussi relié une bande LED.  
C'est aussi le moment de ratacher nos roues aux moteurs, et d'y entourer les elastiques pour pouvoir avoir une meilleur adhérance au sol. 
Nous vous laissons suivre ce schéma pour la construction et la soudure : 

<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/PXL_20240411_121628217.MP.jpg?raw=true" width="445"> 

 Montage | Montage
:-------------------------:|:-------------------------:
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/PXL_20240410_120313893.jpg?raw=true" width="445"> | <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/PXL_20240410_150117329.jpg?raw=true" width="445"> 
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/PXL_20240409_141633069.jpg?raw=truee" width="445"> | <img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/PXL_20240411_085921803.jpg?raw=true" width="445">


## 3. Codage
Pour pouvoir contrôler notre voiture à distance, nous aurons besoin de coder sur Arduino.

Code pour la voiture : Il s'agit du code qui reçoit les infos, qui permet d'allumer et donner de l'energie au moteur, et aussi d'allumer les LED : 

```
#include <ESP8266WiFi.h>
#include <espnow.h>

// REPLACE WITH RECEIVER MAC Address
uint8_t broadcastAddress[] = {0x08,0xF9, 0xE0, 0x73, 0xDC, 0x83};

// Structure example to send data
// Must match the receiver structure
typedef struct struct_message {
  int x;
  int y;
  bool b;
} struct_message;


// Create a struct_message called myData
struct_message myData;

unsigned long lastTime = 0;
unsigned long timerDelay = 300;

void OnDataSent(uint8_t *mac_addr, uint8_t sendStatus) {
  Serial.print("Last Packet Send Status: ");
  if (sendStatus == 0){
    Serial.println("Delivery success");
  }
  else{
    Serial.println("Delivery fail");
  }
}

void setup() {
// Init Serial Monitor
  Serial.begin(74880);
 
  // Set device as a Wi-Fi Station
  WiFi.mode(WIFI_STA);

  // Init ESP-NOW
  if (esp_now_init() != 0) {
    Serial.println("Error initializing ESP-NOW");
    return;
  }

  // Once ESPNow is successfully Init, we will register for Send CB to
  // get the status of Trasnmitted packet
  esp_now_set_self_role(ESP_NOW_ROLE_CONTROLLER);
  esp_now_register_send_cb(OnDataSent);
  
  // Register peer
  esp_now_add_peer(broadcastAddress, ESP_NOW_ROLE_SLAVE, 1, NULL, 0);

  // put your setup code here, to run once:
  pinMode(D1, OUTPUT);
  pinMode(D3, OUTPUT);
  pinMode(D2, INPUT_PULLUP);

}

void loop() {

    digitalWrite(D1, HIGH);
    digitalWrite(D3, LOW);
 
    int av_ar = analogRead(A0);

    digitalWrite(D3, HIGH);
    digitalWrite(D1, LOW);

    int g_d = analogRead(A0);


    // Set values to send
    myData.x = av_ar;
    myData.y = g_d;
    myData.b = true;

    // Send message via ESP-NOW
    esp_now_send(broadcastAddress, (uint8_t *) &myData, sizeof(myData));

    Serial.println(av_ar);
    Serial.println(g_d);
    delay(30);



}
```

Code pour le joytick : Il s'agit du code qui permet de rendre les infos de position de joystick et les transmettre par wifi à la carte de la voiture pour activer ^les mouvement avant/arrière le moteur, ralentir, accélerer, et tourner à droite/gauche

```
#include <ESP8266WiFi.h>
#include <espnow.h>
#include <NeoPixelBus.h>

#define EXPIRE_TIME 10000


const uint16_t PixelCount = 50; // this example assumes 4 pixels, making it smaller will cause a failure
const uint8_t PixelPin = 3; 

#define colorSaturation 128

NeoPixelBus<NeoGrbFeature, NeoWs2812xMethod> strip(PixelCount, PixelPin);

RgbColor red(colorSaturation, 0, 0);
RgbColor green(0, colorSaturation, 0);
RgbColor blue(0, 0, colorSaturation);
RgbColor white(colorSaturation);
RgbColor black(0);
RgbColor pink(229, 0, 109);

HslColor hslRed(red);
HslColor hslGreen(green);
HslColor hslBlue(blue);
HslColor hslWhite(white);
HslColor hslBlack(black);
HslColor hslPink(pink);

// Structure example to receive data
// Must match the sender structure
typedef struct struct_message {
    int x;
    int y;
    bool b;
} struct_message;

// Create a struct_message called myData
struct_message myData;

typedef struct x_y {
  int x = 0;
  int y = 0;
  bool init = false;
} x_y;

x_y offsets;

int ts = 0;

// Callback function that will be executed when data is received
void OnDataRecv(uint8_t * mac, uint8_t *incomingData, uint8_t len) {
  memcpy(&myData, incomingData, sizeof(myData));

 if(!offsets.init){
  offsets.x = myData.x;
  offsets.y = myData.y;
  offsets.init = true;
 }

  myData.x = (myData.x - offsets.x) / 2;
  myData.y = (myData.y - offsets.y) / 2;

  // Serial.print("Bytes received: ");
  // Serial.println(len);
  // Serial.print("X: ");
  // Serial.println(myData.x);
  // Serial.print("Y: ");
  // Serial.println(myData.y);
  // Serial.print("b: ");
  // Serial.println(myData.b);
  // Serial.println();

  if (myData.x > 0){
    analogWrite(D8, myData.x + myData.y);
    analogWrite(D7, 0);
    analogWrite(D6, myData.x - myData.y);
    analogWrite(D5, 0);
  }
  else {
    analogWrite(D8, 0);
    analogWrite(D7, -1*myData.x + myData.y);
    analogWrite(D6, 0);
    analogWrite(D5, -1*myData.x - myData.y);
  }

  ts = millis();
}

void setup() {
  Serial.begin(74880);
  pinMode(D8, OUTPUT);
  pinMode(D7, OUTPUT);
  pinMode(D6, OUTPUT);
  pinMode(D5, OUTPUT);
  pinMode(D2, OUTPUT);

  analogWrite(D8, 0);
  analogWrite(D7, 0);
  analogWrite(D6, 0);
  analogWrite(D5, 0);

  
  // Set device as a Wi-Fi Station
  WiFi.mode(WIFI_STA);

  // Init ESP-NOW
  if (esp_now_init() != 0) {
    Serial.println("Error initializing ESP-NOW");
    return;
  }
  
  // Once ESPNow is successfully Init, we will register for recv CB to
  // get recv packer info
  esp_now_set_self_role(ESP_NOW_ROLE_SLAVE);
  esp_now_register_recv_cb(OnDataRecv);

  while (!Serial); // wait for serial attach

  Serial.println();
  Serial.println("Initializing...");
  Serial.flush();

  // this resets all the neopixels to an off state
   strip.Begin();
  strip.Show();


  Serial.println();
  Serial.println("Running...");
}

void loop() {

  delay(5000);

  Serial.println("Colors R, G, B, W...");

  for(int i = 0; i < PixelCount; ++i){
  strip.SetPixelColor(i, pink);
  }
  strip.Show();

  delay(20);

  if (millis() - ts > EXPIRE_TIME) {
      analogWrite(D8, 0);
      analogWrite(D7, 0);
      analogWrite(D6, 0);
      analogWrite(D5, 0);
  }

  delay(500);

}
```

## 4. Assemblage et personnalisation de la coque
Une fois le montage et le codage terminés, nous pouvons passer à la dernière étape qu'est le montage de tous les élements ensemble et la personnalisation du robot. 

Dans un premier temps, nous avons biens fixé tous nos élements de moteur à une planche de bois de 15cm sur 15cm, que nous avons refermé comme une boite. Nous avons seulement laissé dépassé l'interrupteur pour le rendre facilement accessible, ainsi que la bande LED. 

Pour la personnalisation de Lakitu, nous l'avons d'abord peint avec ses couleurs originales, et nous avons collé la tête au corps. Puis, comme nous volons créer un Lakitu du futur, nous avons construit pleins de petit élements avec du papier aluminium et des fils de fer : des lunettes futuristes, une carapace de cyborg, des câbles, des antennes à la place de ses cheveux ... A vous de laisser libre court à votre imagination ! Il vous suffira de coller tous ces élements grâce avec de la colle chaude. 

Enfin, il est temps de coller le personnage à sa base, en faisant attention de bien placer les LED à l'intérieur du nuage. Pour l'esthétique, nous avons décidé de recouvrir toute la base de boules de cotton, donnant l'impression que notre Lakitu se balade bien dans les nuages !

Notre super voiture est désormais terminée, est prête pour des courses de folies ! 
<img src="https://github.com/Lilousaflower/La_voiture_telecommandee_Latiku_du_futur/blob/IMAGES/lakitu_final_2.png?raw=true">

