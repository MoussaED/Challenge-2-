# Challenge-2-
Challenge 2 VBA assignment_Moussa Diop
' I cannot upload the file for the assignment since it is to big I apologize but with this code provided a copy-paste should have it run normally. 
Sub challenge_2_pt1()

For Each WS In Worksheets
    WS.Activate

'format
 [I1] = "Ticker"
 [J1] = "Yearly change"
 [K1] = "Percent change"
 [L1] = "Total stock volume"
 [Q2] = "Greatest % increase"
 [Q3] = "Greatest % decrease"
 [Q4] = "Greatest total volume"
 [R1] = "Ticker"
 [S1] = "Value"
Columns("A:S").AutoFit
Columns("K").NumberFormat = "0.00%"
Columns("J").NumberFormat = "0.00"

Dim Ticker As String
Dim Ticker_column As Integer
Dim Stock_volume As Double
Dim Stock_volume_column As Double

Dim Open_value As Single
Dim Closed_value As Single
Dim Value_column As Integer
Dim Yearly_change As Double

Dim Percent_column As Single
Dim Percent_change As Double


Stock_volume = 0
Ticker_column = 2
Stock_volume_column = 2
Open_value = Cells(2, 3).Value
Closed_value = 0
Value_column = 2
Yearly_change = 0
Percent_change = 0
Percent_column = 2


For i = 2 To 753000


'if cells dont equal then
    If Cells(i + 1, 1).Value <> Cells(i, 1).Value Then
                 
                
        'Ticker name code
                Ticker = Cells(i, 1).Value
        
                Range("I" & Ticker_column).Value = Ticker
        
                Ticker_column = Ticker_column + 1
            
        ' stock volume print
                Stock_volume = Cells(i, 7).Value + Stock_volume
                
                Range("L" & Stock_volume_column).Value = Stock_volume
            
                Stock_volume_column = Stock_volume_column + 1
        'Yearly change Code
            Closed_value = Cells(i, 6).Value
        
                Yearly_change = Closed_value - Open_value
                
                Range("j" & Value_column).Value = Yearly_change
                
                ' Formating color
                    If Yearly_change >= 0 Then
                        Range("j" & Value_column).Interior.ColorIndex = 4
             
                    Else
                        Range("j" & Value_column).Interior.ColorIndex = 3
                        
                End If
                        
                Value_column = Value_column + 1
        'Percent change code
        
                Percent_change = 1 - (Closed_value / Open_value)
                
                Percent_change = Percent_change * -1
                
                
                Range("k" & Percent_column).Value = Percent_change
            Cells(i, 11).NumberFormat = "0.00%"
                
                Percent_column = Percent_column + 1
                
                
                
' reset stock volume/Open_value
        Stock_volume = 0
        Open_value = Cells(i + 1, 3).Value
' if cells are equal then
    Else
    'stock volume code
          Stock_volume = Cells(i, 7).Value + Stock_volume
            
    
    End If

Next i
        

Dim Greatest_inc As Single
Dim Greatest_dec As Single
Dim Greatest_vol As Double


For i = 2 To 3000
     If Cells(i, 11) > Greatest_inc Then
        Greatest_inc = Cells(i, 11).Value
        
        Cells(2, 19).Value = Greatest_inc
        Cells(2, 18).Value = Cells(i, 9).Value
        
    ElseIf Cells(i, 11) < Greatest_dec Then
    
        Greatest_dec = Cells(i, 11).Value
        
        Cells(3, 19).Value = Greatest_dec
        Cells(3, 18).Value = Cells(i, 9).Value
        
    ElseIf Cells(i, 12) > Greatest_vol Then
    
        Greatest_vol = Cells(i, 12).Value
        
        Cells(4, 19).Value = Greatest_vol
        Cells(4, 18).Value = Cells(i, 9).Value
        
    End If

Next i
            
            
            
Next WS
            
            
End Sub


MaSub challenge_2_pt2()


Dim Greatest_inc As Single
Dim Greatest_dec As Single
Dim Greatest_vol As Double


For i = 2 To 3000
     If Cells(i, 11) > Greatest_inc Then
        Greatest_inc = Cells(i, 11).Value
        
        Cells(2, 19).Value = Greatest_inc
        Cells(2, 18).Value = Cells(i, 9).Value
        
    ElseIf Cells(i, 11) < Greatest_dec Then
    
        Greatest_dec = Cells(i, 11).Value
        
        Cells(3, 19).Value = Greatest_dec
        Cells(3, 18).Value = Cells(i, 9).Value
        
    ElseIf Cells(i, 12) > Greatest_vol Then
    
        Greatest_vol = Cells(i, 12).Value
        
        Cells(4, 19).Value = Greatest_vol
        Cells(4, 18).Value = Cells(i, 9).Value
        
    End If

Next i
            
            
            

End Sub 























