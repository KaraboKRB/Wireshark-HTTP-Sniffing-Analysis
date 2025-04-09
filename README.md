# Wireshark-HTTP-Sniffing-Analysis

# **Wireshark HTTP Packet Sniffing Analysis**  
_A practical demonstration of intercepting unencrypted HTTP traffic._  

## **Objective**  
Capture and analyze plaintext HTTP traffic (including login credentials) using Wireshark.  

## **Steps to Reproduce**  
1. **Setup**  
   - Install [Wireshark](https://www.wireshark.org/).  
   - Start capturing on your network interface (Wi-Fi/Ethernet).  

2. **Generate HTTP Traffic**  
   - Visit `http://testphp.vulnweb.com/login.php`.  
   - Enter test credentials (`test:test`).  

3. **Analyze in Wireshark**  
   - Apply filter: `http(ip.sec == 194.253.249.114 || ip.dst == 194.253.249.114 )`.  
   - More filter that i like `http.request.method == "POST"`
   - Follow the TCP stream to see raw credentials.  

## **Key Findings**  
 - Captured plaintext credentials in HTTP POST requests.  
 - Observed DNS queries leaking visited domains.  
 - Demonstrated risks of unencrypted web traffic.  

## **Security Recommendations**  
- Always use **HTTPS** instead of HTTP.  
- Avoid entering passwords on non-HTTPS sites.  
- Use a **VPN** on public networks.  

## **Files**  
- `captures/http_login_capture.pcapng` – Sample Wireshark capture.  
- `screenshots/http_credentials.png` – Exposed credentials in HTTP.  
