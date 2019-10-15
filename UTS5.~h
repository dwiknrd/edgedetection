//---------------------------------------------------------------------------

#ifndef UTS5H
#define UTS5H
//---------------------------------------------------------------------------
#include <Classes.hpp>
#include <Controls.hpp>
#include <StdCtrls.hpp>
#include <Forms.hpp>
#include <ExtCtrls.hpp>
#include <Dialogs.hpp>
#include <ExtDlgs.hpp>
#include <Chart.hpp>
#include <Series.hpp>
#include <TeEngine.hpp>
#include <TeeProcs.hpp>
#define TMX 2000
//---------------------------------------------------------------------------
class TForm1 : public TForm
{
__published:	// IDE-managed Components
        TImage *Image1;
        TBevel *Bevel1;
        TStaticText *StaticText1;
        TPanel *Panel1;
        TImage *Image2;
        TPanel *Panel2;
        TImage *Image3;
        TButton *Button1;
        TBevel *Bevel2;
        TStaticText *StaticText2;
        TStaticText *StaticText3;
        TBevel *Bevel3;
        TOpenPictureDialog *OpenPictureDialog1;
        TButton *Button2;
        TButton *Button3;
        TButton *Button4;
        TButton *Button5;
        TChart *Chart1;
        TImage *GarisPandu;
        TImage *GarisPandu2;
        TLineSeries *Series2;
        TLineSeries *Series3;
        void __fastcall Image1Click(TObject *Sender);
        void __fastcall Button1Click(TObject *Sender);
        void __fastcall LaplacianDetect(TObject *Sender);
        void __fastcall SmoothingDetect(TObject *Sender);
        void __fastcall SobelDetect(TObject *Sender);
        void __fastcall PrewittDetect(TObject *Sender);
        void __fastcall GarisPanduOnMouseMove(TObject *Sender,
          TShiftState Shift, int X, int Y);
private:	// User declarations
public:
        AnsiString FileAsli;
        int height;
        int width;

        int x;
        int y;
        int lebar_f, tinggi_f;
        float d_lebar, d_tinggi;

        Byte *citra [TMX];
        Byte *citra2 [TMX];		// User declarations
        __fastcall TForm1(TComponent* Owner);
        void __fastcall Siapkan(Byte *img[TMX]);
        void __fastcall Bersihkan(Byte *img[TMX], int v);
        void __fastcall Laplacian(Byte *img[TMX], Byte *img2[TMX]);
        void __fastcall TampilCitra(Byte *img[TMX], TImage * Image);
        void __fastcall Smoothing(Byte *img[TMX], Byte *img2[TMX]);
        void __fastcall Sobel(Byte *img[TMX], Byte *img2[TMX]);
        void __fastcall Prewitt(Byte *img[TMX], Byte *img2[TMX]);
};
//---------------------------------------------------------------------------
extern PACKAGE TForm1 *Form1;
//---------------------------------------------------------------------------
#endif
