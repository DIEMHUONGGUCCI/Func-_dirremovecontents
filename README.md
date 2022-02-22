Local $search, $file
	If StringRight($folder, 1) <> "\" Then $folder = $folder & "\"
	$search = FileFindFirstFile($folder & "*.*")
	If $search = -1 Then Return 0
	While 1
		$file = FileFindNextFile($search)
		If StringRight($file, 1) = "." Then ContinueLoop
		If FileGetAttrib($folder & $file) = "D" Then DirRemove($folder & $file, 1)
	WEnd
	FileClose($search)
EndFunc
