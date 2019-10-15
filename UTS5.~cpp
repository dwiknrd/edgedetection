//---------------------------------------------------------------------------

#include <vcl.h>
#pragma hdrstop

#include "UTS5.h"
#include <jpeg.hpp>
//---------------------------------------------------------------------------
#pragma package(smart_init)
#pragma resource "*.dfm"
TForm1 *Form1;
//---------------------------------------------------------------------------
__fastcall TForm1::TForm1(TComponent* Owner)
        : TForm(Owner)
{
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Image1Click(TObject *Sender)
{
TJPEGImage *jpeg = new TJPEGImage;
Image1->Picture->LoadFromFile("Header.jpg");
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Button1Click(TObject *Sender)
{
if (OpenPictureDialog1->Execute()){

    	FileAsli = OpenPictureDialog1->Files->Strings[0].c_str();
    	Image2->Picture->LoadFromFile(OpenPictureDialog1->FileName);
    
    	Graphics::TBitmap *Bitmap = new Graphics::TBitmap();
        	Bitmap->LoadFromFile(OpenPictureDialog1->FileName);
    	
height = Bitmap->Height;
    	width = Bitmap->Width;

    	Siapkan(citra); Bersihkan(citra,0);      // maksudnya nol adalah pengisi y
      	
for(int i=0;i<height;i++){
        		for(int j=0;j<width;j++){
          			citra[i][j] = Bitmap->Canvas->Pixels[j][i];
        		}
      	}
    }
        
}
//---------------------------------------------------------------------------


void __fastcall TForm1::Siapkan(Byte *img[TMX])
{
for (int i=0;i<height;i++){
    	img[i]= new Byte [width];
   	if (img[i]==NULL){
      		Application->MessageBox("Terjadi Kesalahan!","ERROR!",MB_OKCANCEL);
    	}
  }        //TODO: Add your source code here
}

void __fastcall TForm1::Bersihkan(Byte *img[TMX], int v)
{
for(int i=0;i<height;i++)
    for(int j=0;j<width;j++)
      img[i][j]=v;         //TODO: Add your source code here
}
void __fastcall TForm1::LaplacianDetect(TObject *Sender)
{
Laplacian(citra,citra2);
TampilCitra(citra2,Image3);
}
//---------------------------------------------------------------------------


void __fastcall TForm1::Laplacian(Byte *img[TMX], Byte *img2[TMX])
{
 short int temp;
 Siapkan(img2); Bersihkan(img2,0);

 for(int i=1;i<(height-1);i++){
       for(int j=1;j<(width-1);j++){
           temp=(-1*img[i-1][j-1])+(0*img[i-1][j])+(-1*img[i-1][j+1])
               +(0*img[i][j-1])+(4*img[i][j])+(0*img[i][j+1])
               +(-1*img[i+1][j-1])+(0*img[i+1][j])+(-1 *img[i+1][j+1]);
       if(temp>=255)img2[i][j]=255;
       else if(temp<=0)img2[i][j]=0;
       else img2[i][j]=temp;
   }
 }        //TODO: Add your source code here
}

void __fastcall TForm1::TampilCitra(Byte *img[TMX], TImage * Image)
{
 Byte temp;

 int px, py;
 int w=Image->Width;
 int h=Image->Height;

 float dx=(float)w/width;
 float dy=(float)h/height;

 Image->Picture=NULL;
 for(int i=0; i<h; i++){
  py=i/dy;
  for(int j=0; j<w; j++){
   px=j/dx;
   temp=img[py][px];
   SetPixel(Image->Canvas->Handle,j,i,RGB(temp,temp,temp));
  }
 }        //TODO: Add your source code here
}
void __fastcall TForm1::SmoothingDetect(TObject *Sender)
{
Smoothing(citra,citra2);
TampilCitra(citra2,Image3);
}
//---------------------------------------------------------------------------


void __fastcall TForm1::Smoothing(Byte *img[TMX], Byte *img2[TMX])
{
short int temp;
Siapkan(img2);
Bersihkan(img2,0);

for(int i=1;i<(height-1);i++){
for(int j=1;j<(width-1);j++){

temp=(float)1/16*(1*citra[i-1][j-1]+2*citra[i-1][j]+1*citra[i-1][j+1]
+2*citra[i][j-1]+4*citra[i][j]+2*citra[i][j+1]
+1*citra[i+1][j-1]+2*citra[i+1][j]+1*citra[i+1][j+1]);

if(temp>=255)img2[i][j]=255;
else if(temp<=0)img2[i][j]=0;
img2[i][j]=temp;
}
}
}        //TODO: Add your source code here

void __fastcall TForm1::SobelDetect(TObject *Sender)
{
Sobel(citra,citra2);
TampilCitra(citra2,Image3);
}
//---------------------------------------------------------------------------


void __fastcall TForm1::Sobel(Byte *img[TMX], Byte *img2[TMX])
{
 short int temp;
 short int tempX;
 short int tempY;
 Siapkan(img2); Bersihkan(img2,0);

 for(int i=1;i<(height-1);i++){
       for(int j=1;j<(width-1);j++){
           tempX=(-1*img[i-1][j-1])+(0*img[i-1][j])+(1*img[i-1][j+1])
               +(-2*img[i][j-1])+(0*img[i][j])+(2*img[i][j+1])
               +(-1*img[i+1][j-1])+(0*img[i+1][j])+(1*img[i+1][j+1]);

           tempY=(-1*img[i-1][j-1])+(-2*img[i-1][j])+(-1*img[i-1][j+1])
               +(0*img[i][j-1])+(0*img[i][j])+(0*img[i][j+1])
               +(1*img[i+1][j-1])+(2*img[i+1][j])+(1*img[i+1][j+1]);

           temp=abs(tempX) + abs(tempY);

       if(temp>=255)img2[i][j]=255;
       else if(temp<=0)img2[i][j]=0;
       else img2[i][j]=temp;
   }
 }        //TODO: Add your source code here
}
void __fastcall TForm1::PrewittDetect(TObject *Sender)
{
Prewitt(citra,citra2);
TampilCitra(citra2,Image3);
}
//---------------------------------------------------------------------------


void __fastcall TForm1::Prewitt(Byte *img[TMX], Byte *img2[TMX])
{
 short int temp;
 short int tempX;
 short int tempY;
 Siapkan(img2); Bersihkan(img2,0);

 for(int i=1;i<(height-1);i++){
       for(int j=1;j<(width-1);j++){
           tempX=(-1*img[i-1][j-1])+(0*img[i-1][j])+(1*img[i-1][j+1])
               +(-1*img[i][j-1])+(0*img[i][j])+(1*img[i][j+1])
               +(-1*img[i+1][j-1])+(0*img[i+1][j])+(1*img[i+1][j+1]);

           tempY=(-1*img[i-1][j-1])+(-1*img[i-1][j])+(-1*img[i-1][j+1])
               +(0*img[i][j-1])+(0*img[i][j])+(0*img[i][j+1])
               +(1*img[i+1][j-1])+(1*img[i+1][j])+(1*img[i+1][j+1]);

           temp=abs(tempX) + abs(tempY);

       if(temp>=255)img2[i][j]=255;
       else if(temp<=0)img2[i][j]=0;
       else img2[i][j]=temp;
   }
 }        //TODO: Add your source code here
}

void __fastcall TForm1::GarisPanduOnMouseMove(TObject *Sender,
      TShiftState Shift, int X, int Y)
{
	if (width!=0){
	  lebar_f =Image2->Width; // w = lebar bingkai di form
	  tinggi_f =Image2->Height;

	  d_lebar=(float)lebar_f/width; // width = lebar piksel gambar
	  d_tinggi=(float)tinggi_f/height;

	  int Xreal;
	  Xreal=X/d_lebar;

	  int Yreal;
	  Yreal=Y/d_tinggi;

	  Series2->Clear();
	  for(int a=0;a<width;a++){
	  Series2->AddY(citra[Yreal][a],"",clRed);
	}
	  Series3->Clear();
	  for(int a=0;a<width;a++){
	  Series3->AddY(citra2[Yreal][a],"",clBlue);
	}
	  GarisPandu->Canvas->FillRect(ClientRect);
	  GarisPandu->Canvas->Pen->Color=clRed;
	  GarisPandu->Canvas->MoveTo(0,Y);
	  GarisPandu->Canvas->LineTo(GarisPandu->Width,Y);
	  GarisPandu->Canvas->MoveTo(X,0);
	  GarisPandu->Canvas->LineTo(X,GarisPandu->Height);
	  GarisPandu2->Canvas->FillRect(ClientRect);
	  GarisPandu2->Canvas->Pen->Color=clBlue;
	  GarisPandu2->Canvas->MoveTo(0,Y);
	  GarisPandu2->Canvas->LineTo(GarisPandu->Width,Y);
	  GarisPandu2->Canvas->MoveTo(X,0);
	  GarisPandu2->Canvas->LineTo(X,GarisPandu->Height);

	  //Label1->Caption=citra[Yreal][Xreal];
	  //Label2->Caption=Xreal;
	  //Label3->Caption=Yreal;
    }
}
//---------------------------------------------------------------------------

