unit Unit1;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, Forms, Controls, Graphics, Dialogs, StdCtrls;

type

  { TForm1 }

  TForm1 = class(TForm)
    btnConverter: TButton;
    campoTemp: TEdit;
    titulo: TLabel;
    txtTemp: TLabel;
    instrucao: TLabel;
    descricao: TLabel;
    cel: TRadioButton;
    fah: TRadioButton;
    procedure btnConverterClick(Sender: TObject);
  private

  public

  end;

var
  Form1: TForm1;
  txtTemp: double;
  formulaCel: double;
  formulaFah: double;

implementation

{$R *.lfm}

{ TForm1 }

procedure TForm1.btnConverterClick(Sender: TObject);
begin
  try
      // Fórmula: F = (C * 1.8) + 32
      if cel.checked then
         begin
           formulaCel := (StrToFloat(campoTemp.text) * 1.8) + 32;
           instrucao.caption := 'A temperatura em Fahrenheit é ' + FloatToStr(formulaCel) + ' F° !';
         end

      // Formula: T = (F - 32) × 5/9
      else if fah.checked then
         begin
           formulaFah := (StrToFloat(campoTemp.text) - 32) * 5 / 9;
           instrucao.caption := 'A temperatura em Celsius é ' + FloatToStr(formulaFah) + ' C° !';
         end;

      campoTemp.SetFocus;
      campoTemp.text := '';

  except
    on E: Exception do
      ShowMessage('Digite um número válido para a temperatura.');
  end;

end;

end.
