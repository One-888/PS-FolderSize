function Get-FolderSize
# https://devblogs.microsoft.com/scripting/weekend-scripter-use-powershell-to-get-folder-sizes/
{

	begin{$fso = New-Object -comobject Scripting.FileSystemObject}

	process{

		$path = $Input.fullname
        $path1 = Split-Path -Path $path -Leaf

		$folder = $fso.GetFolder($path)

		$size = $folder.size
        $name = $folder.name

		[PSCustomObject]@{'Name' = $name
                          'Size' = “{0:N2}” -f ($size / 1gb)
                          'Path' = $path 
                      }
                         
           }
                      
}

Get-ChildItem -Directory -Recurse -EA 0 -Depth 0 | Get-FolderSize | select -First 25 | sort size -Descending | Format-Table -AutoSize
