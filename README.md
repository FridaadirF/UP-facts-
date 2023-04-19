
//start program

PImage photo; // lande billede


PImage[] landeFlag;

float aktuelFarve=0; //den aktuelle farve sammensætning som musen klikker på
float[] landeKode; //værdien farven af landet
String[] landeNavn; //navnet tilhørende farven
String[] landeAreal; //arealet tilhørende landet
String[] landeIndbygger;
int foersteStart=1; //startskærm
int nyLand=0; //indikere at der er sket ændringer, når musen er trykket så skal draw tegne nyt billede
int musX=0; //mus start x-værdi
int musY=0;//mus start y-værdi
int landIndex=0; //gemmer og overfører farvenummeret af det aktuelle land til draw




//denne del tager RGB farvesammensætningen fra den aktuelle farve som musen klikker på og danner en unik farvekode
public void mouseMoved()
{
  //kilde...
  aktuelFarve=blue(get().pixels[mouseX + mouseY * width]); // finder det aktuelle indhold af blå på billedet
  aktuelFarve=aktuelFarve*256+green(get().pixels[mouseX + mouseY * width]); // ganger den blå værdi med 256 (antal mulige farver) og lægger den grønne værdi til
  aktuelFarve=aktuelFarve*256+red(get().pixels[mouseX + mouseY * width]); // ganger den foregående værdi med 256 og lægger den røde værdi til
}


//brugte vi til at finde de forskellige farvers kode
//public void mouseClicked() //hvis man klikker så...
//{
//  println("Farvekode: "+aktuelFarve); //giver programmet den aktuelle farve tilbage som "Farvekode; xxxxx"
//}





//setup af programmet( skaber vindue, definere indholdet af varibalerne)
void setup () {
  size(1812, 832);//størrelse af skærm

  photo = loadImage ("FarvedeKort.png"); //henter verdens billedet
  photo.resize(1812, 832);
  
  

  landeKode = new float[23];  //ande farve værdi
  landeNavn = new String[23]; // landets navm tilhørende værdien
  landeAreal = new String[23];
  landeIndbygger = new String[23];
  landeFlag = new PImage[23];
  

  landeKode[0]=1.6773836E7; //nummeret
  landeNavn[0]="Ocean";  //navnet

  landeKode[1]=4905210;
  landeNavn[1]="Russia";
  landeAreal[1]="Area: 17.098.242 km²";
  landeIndbygger[1]="Population: 143,4 mio";
  landeFlag[1]= loadImage ("russia.png");
  landeFlag[1].resize(274, 149);

  landeKode[2]=4819949;
  landeNavn[2]="Canada";
  landeAreal[2]="Area: 9.984.670 km²";
  landeIndbygger[2]="Population: 38,25 mio";

  landeKode[3]=4872416;
  landeNavn[3]="China";
  landeAreal[3]="Area: 9.706.961 km²";
  landeIndbygger[3]="Population: 1,412 mia";

  landeKode[4]=4904108;
  landeNavn[4]="United States of America";
  landeAreal[4]="Area: 9.372.610 km²";
  landeIndbygger[4]="Population: 331,9 mio";


  landeKode[5]=4819945;
  landeNavn[5]="Brazil";
  landeAreal[5]="Area: 8.515.767 km²";
  landeIndbygger[5]="Population: 214,3 mio";

  landeKode[6]=4899444;
  landeNavn[6]="Australia";
  landeAreal[6]="Area: 7.692.024 km²";
  landeIndbygger[6]="Population: 25.69 mio";

  landeKode[7]=4905209;
  landeNavn[7]="India";
  landeAreal[7]="Area: 3.287.590 km²";
  landeIndbygger[7]="Population: 1,408 mia";

  landeKode[8]=4901616;
  landeNavn[8]="Argentina";
  landeAreal[8]="Area: 2.780.400 km²  ";
  landeIndbygger[8]="Population: 45,81 mio";

  landeKode[9]=4819943;
  landeNavn[9]="Kazakhstan";
  landeAreal[9]="Areal: 2.724.900 km²";
  landeIndbygger[9]="Population: 19 mio";

  landeKode[10]=4904688;
  landeNavn[10]="Algeria";
  landeAreal[10]="Area: 2.381.741 km²";
  landeIndbygger[10]="Population: 44,18 mio";

  landeKode[11]=4818150;
  landeNavn[11]="Democratic Rep. Congo";
  landeAreal[11]="Area: 2.34.858 km²  ";
  landeIndbygger[11]="Population: 95,89 mio";

  landeKode[12]=4902384;
  landeNavn[12]="Mexico";
  landeAreal[12]="Area: 1.964.375 km²";
  landeIndbygger[12]="Population: 126.7 mio";

  landeKode[13]=4870620;
  landeNavn[13]="Saudi Arabia";
  landeAreal[13]="Area: 2.149.690 km²";
  landeIndbygger[13]="Population: 35,95 mio";

  landeKode[14]=4819430;
  landeNavn[14]="Indonesia";
  landeAreal[14]="Area: 1.904.569 km²";
  landeIndbygger[14]="Population: 272,8 mio";

  landeKode[15]=4902048;
  landeNavn[15]="Sudan";
  landeAreal[15]="Areal: 1.886.068 km²";
  landeIndbygger[15]="Population: 45,66 mio";

  landeKode[16]=4631140;
  landeNavn[16]="Libya";
  landeAreal[16]="Area: 1.759.540 km²";
  landeIndbygger[16]="Population: 6,735 mio";

  landeKode[17]=4905208;
  landeNavn[17]="Iran";
  landeAreal[17]="Area: 1.648.195 km²";
  landeIndbygger[17]="Population: 87,92 mio";

  landeKode[18]=4904107;
  landeNavn[18]="Peru";
  landeAreal[18]="Area: 1.285.216 km²";
  landeIndbygger[18]="Population: 33,72 mio";


  landeKode[19]=4905201;
  landeNavn[19]="Chad";
  landeAreal[19]="Area: 1.284.000 km²";
  landeIndbygger[19]="Population: 17,18 mio";

  landeKode[20]=4904102;
  landeNavn[20]="Mongolia";
  landeAreal[20]="Area: 1.564.110 km²";
  landeIndbygger[20]="Population: 3,348 mio";

  landeKode[21]=4636265;
  landeNavn[21]="Denmark";
  landeAreal[21]="Area: 43.094 km²";
  landeIndbygger[21]="Population: 5,857 mio";

  landeKode[22]=4904109;
  landeNavn[22]="Greenland";
  landeAreal[22]="Area: 2.166.000 km²";
  landeIndbygger[22]="Population: 56.653";
  landeFlag[22]= loadImage ("grøndland.jpeg");
  landeFlag[22].resize(274, 149);
}


//denne del kan man
void draw() {
  if (foersteStart==1) {
    background(189, 231, 250); //baggrundfarve
    image(photo, 0, 0); //tegner billede i punktet 0,0
    foersteStart=0; //sætter dette til
  } else {
    if (nyLand==1) {
      background(189, 231, 250); //baggrundfarve
      image(photo, 0, 0); //tegner billede i punktet 0,0
      

      fill(255, 255, 255);
      rect(37, 400, 275, 400);
      line(37, 440, 312, 440);
      line(37, 492, 312, 492);
      line(37, 544, 312, 544);
      line(37, 596, 312, 596);
      line(37, 650, 312, 650);
      if(landeFlag[landIndex] == null) {rect(37,650,275,150);} else {image(landeFlag[landIndex], 38,651);} 

      nyLand=0;//


      fill(0);
      textSize(25);
      text(landeNavn[landIndex], 50, 430); //
      text(landeAreal[landIndex], 50, 475);
      text(landeIndbygger[landIndex], 50, 529); //
    }
  }
}



void mousePressed() {
  for (int i = 0; i <23; i++) {//dette definere i til at kunne være alle de forskellige landes værdier
    if (aktuelFarve==landeKode[i]) { //hvis den aktuelle farve er lig med et at landene farve, så dukker landets navn op
      // println(landeNavn[i]); //så skriv landets navn

      if (aktuelFarve==landeKode[0]) { //hvis man trykker på oceanet så skal navnet forsvinde, da man kommer tilbage til startskærmen
        nyLand=0;
        foersteStart=1;
      } else {


        // text(landeNavn[i],174,400); //ellers så dukker landets navn op, der hvor man trykkede



        nyLand=1;
        musX = mouseX;
        musY = mouseY;
        landIndex=i;
      }
    }
  }
}
