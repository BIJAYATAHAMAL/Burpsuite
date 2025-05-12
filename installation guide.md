

## **1. Installing Burp Suite (Community Edition)**

###  **On Windows / Linux / macOS:**

#### **Step 1: Download Burp Suite**

* Go to the official PortSwigger website:
  🔗 [https://portswigger.net/burp](https://portswigger.net/burp)
* Click on **“Download”** under **Community Edition**.

#### **Step 2: Install Burp Suite**

* For **Windows**: Run the downloaded `.exe` installer.
* For **Linux**:
  If you downloaded the `.sh` file, open a terminal and run:

  ```bash
  chmod +x burpsuite_community_linux.sh
  ./burpsuite_community_linux.sh
  ```
* For **macOS**: Open the `.dmg` file and drag Burp Suite into Applications.

---

##  **2. Configure Browser with Burp Suite (using Firefox)**

### **Step 1: Set up Burp Proxy in Firefox**

* Open Firefox.
* Go to **Settings > Network Settings > Manual Proxy Configuration**:

  * HTTP Proxy: `127.0.0.1`
  * Port: `8080`
  * Check: "Use this proxy server for all protocols"
* Click **OK**.

### **Step 2: Install Burp's CA Certificate (Important for HTTPS)**

1. Open Firefox and go to:
   `http://burpsuite`
2. Click on **CA Certificate** to download it.
3. Go to **Firefox Settings > Privacy & Security > Certificates > View Certificates > Authorities**.
4. Click **Import**, select the downloaded certificate, and check:

   * Trust this CA to identify websites.

---

##  **3. How to Use Burp Suite for Parameter Tampering**

### **Scenario: Changing Course Cost on Afa India Website**

#### **Step-by-step:**

1. **Start Burp Suite** (Community Edition is fine).
2. Click **Proxy > Intercept** → Make sure Intercept is **ON**.
3. Open Firefox (already configured to use Burp).
4. Go to the Afa India registration page.
5. Fill in all the required registration details (name, email, etc.).
6. **Click the Register/Submit button** – this triggers a POST request.
7. Burp Suite will **intercept the request**.
8. In the intercepted HTTP request, look for **parameters like `course_price=10000`**.
9. **Modify the value**, for example: `course_price=1000`.
10. Click **Forward** to send the modified request to the server.

This process is called **parameter tampering** – altering values passed through the client-side to trick the server.

