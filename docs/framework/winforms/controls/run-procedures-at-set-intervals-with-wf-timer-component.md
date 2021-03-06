---
title: 'Gewusst wie: Ausführen von Prozeduren in festgelegten Abständen mit der Timer-Komponente in Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: bf0e22eab3b6517521dbe06a73f63af232746df1
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339265"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Gewusst wie: Ausführen von Prozeduren in festgelegten Abständen mit der Timer-Komponente in Windows Forms
In einigen Fällen möchten Sie möglicherweise eine Prozedur erstellen, die entweder in bestimmten Zeitintervallen bis zum Ende einer Schleife oder nach Ablauf eines festgelegten Zeitintervalls ausgeführt wird. Die <xref:System.Windows.Forms.Timer>-Komponente ermöglicht eine solche Prozedur.  
  
 Diese Komponente wurde für eine Windows Forms-Umgebung entwickelt. Wenn Sie einen für eine Serverumgebung geeigneten Timer benötigen, lesen Sie die Informationen unter [Introduction to Server-Based Timers (Einführung in serverbasierte Timer)](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Die Verwendung der <xref:System.Windows.Forms.Timer>-Komponente unterliegt einigen Einschränkungen. Weitere Informationen finden Sie unter [Einschränkungen für die Windows Forms Timer-Komponente Interval-Eigenschaft](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>So führen Sie eine Prozedur in festgelegten Intervallen mit der Timer-Komponente aus  
  
1.  Fügen Sie Ihrem Formular einen <xref:System.Windows.Forms.Timer> hinzu. Im folgenden Beispielabschnitt finden Sie eine Abbildung zur entsprechenden programmgesteuerten Vorgehensweise. Visual Studio bietet auch Unterstützung für das Hinzufügen von Komponenten zu einem Formular. Siehe auch [Vorgehensweise: Hinzufügen Steuerelementen ohne Benutzeroberfläche zu Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Legen Sie die <xref:System.Windows.Forms.Timer.Interval%2A>-Eigenschaft (in Millisekunden) für den Zeitgeber fest. Diese Eigenschaft bestimmt, in welchem Zeitabstand die Prozedur erneut ausgeführt werden soll.  
  
    > [!NOTE]
    >  Je öfter ein Zeitgeberereignis auftritt, desto mehr Prozessorzeit wird für die Reaktion auf das Ereignis aufgewendet. Dadurch kann sich die Gesamtleistung verringern. Legen Sie kein kleineres Intervall als erforderlich fest.  
  
3.  Schreiben Sie den entsprechenden Code in den <xref:System.Windows.Forms.Timer.Tick> Ereignishandler. Der in dieses Ereignis geschriebene Code wird in dem in der <xref:System.Windows.Forms.Timer.Interval%2A>-Eigenschaft angegebenen Intervall ausgeführt.  
  
4.  Legen Sie die <xref:System.Windows.Forms.Timer.Enabled%2A>-Eigenschaft auf `true` fest, um den Zeitgeber zu starten. Das <xref:System.Windows.Forms.Timer.Tick>-Ereignis tritt nun ein und führt die Prozedur im festgelegten Intervall aus.  
  
5.  Legen Sie die <xref:System.Windows.Forms.Timer.Enabled%2A>-Eigenschaft zu gegebener Zeit auf `false` fest, um die weitere Ausführung der Prozedur zu verhindern. Festlegen des Intervalls auf `0` bewirkt nicht, dass den Zeitgeber zu beenden.  
  
## <a name="example"></a>Beispiel  
 In diesem ersten Codebeispiel wird die Tageszeit in 1-Sekunden-Schritten erfasst. Darin werden Komponenten vom Typ <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label> und <xref:System.Windows.Forms.Timer> in einem Formular verwendet. Die <xref:System.Windows.Forms.Timer.Interval%2A>-Eigenschaft ist auf 1000 (entspricht einer Sekunde) festgelegt. Im <xref:System.Windows.Forms.Timer.Tick>-Ereignis ist die Beschriftung der Label-Komponente auf die aktuelle Zeit festgelegt. Wenn Sie auf die Schaltfläche klicken, wird die <xref:System.Windows.Forms.Timer.Enabled%2A>-Eigenschaft auf `false` festgelegt, sodass der Zeitgeber die Beschriftung der Label-Komponente nicht mehr aktualisiert. Im folgenden Codebeispiel erfordert, dass ein Formular mit einem <xref:System.Windows.Forms.Button> Steuerelement mit dem Namen `Button1`, <xref:System.Windows.Forms.Timer> Steuerelement mit dem Namen `Timer1`, und ein <xref:System.Windows.Forms.Label> Steuerelement mit dem Namen `Label1`.  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>Beispiel  
 In diesem zweiten Codebeispiel wird eine Prozedur alle 600 Millisekunden bis zum Ende einer Schleife ausgeführt. Im folgenden Codebeispiel erfordert, dass ein Formular mit einem <xref:System.Windows.Forms.Button> Steuerelement mit dem Namen `Button1`, <xref:System.Windows.Forms.Timer> Steuerelement mit dem Namen `Timer1`, und ein <xref:System.Windows.Forms.Label> Steuerelement mit dem Namen `Label1`.  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.Timer>  
 [Timer-Komponente](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Übersicht über die Timer-Komponente](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
