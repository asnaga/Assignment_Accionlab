# Assignment_Accionlab
Text Manipulation Problem

#Problem: Extract unique IP addresses that caused a 404 error:
#Tool/commands using: grep (filter lines with 404) awk (Extract IP) sort & uniq -c (count occurences)


#Solution
grep " 404 " access.log | awk '{print $1}' | sort | uniq -c | sort -nr

#grep will find lines with 404 errors
#awk will extract the IP address
# sort | uniq -c Count uinque Ip occurences
# sort -nr will sort in descending order by count
