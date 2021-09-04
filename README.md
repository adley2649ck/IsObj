# IsObj
; Name...........: x_count ; Description ...: Returns a count of items ; Syntax.........: x_count( $sKey ) ; Parameters ....: $sKey - the key ; Return values .: Success: count of items of a provided key ;                           x_count() returns count os keys on first level ;                  Failure: 0, set error to: ;                                -1 = the key is not an object, but an item with a value ;                                -2 = the key does not exist ; Author ........:  shEiD (original "x" UDF by: OHB) Func x_count($sKey = '')     If $sKey == '' Then Return $_xHashCollection.Count     Local $cur = $_xHashCollection     Local $parts = StringSplit($sKey, ".")     For $x = 1 To $parts[0]         If Not $cur.exists($parts[$x]) Then Return SetError(-2, 0, 0)         $cur = $cur.item($parts[$x])     Next     If Not IsObj($cur) Then SetError(-1, 0, 0)     Return $cur.Count EndFunc   ;==>x_count
