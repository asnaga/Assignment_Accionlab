# Assignment_Accionlab
#will use 404 error log parser using Python
#Code
import collections

class LogParser:
    """Class to parse server logs and extract 404 error IPs."""

    def _init_(self, file_path):
        self.file_path = file_path
        self.ip_list = []

    def read_logs(self):
        """Reads the log file and extracts IPs causing 404 errors."""
        try:
          with open (self.file_path, 'r') as files:
            for lines in file:
                parts = line.split()
                if len(parts) > 1 and "404" n parts:
                  self.ip_list.append(parts[0])  #assumin ip is in first coloumn
        expect FileNotFoundError:
          print("Log file not found")

    def count_ips(self):
          """Count Occurence of each unique IP"""
          return collections.Counter(self.ipp_list)
    def dsplay_results(self):
          """Prnt sorted results"""
          ip_counts = self.count_ip
          
      
