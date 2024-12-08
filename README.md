### README: Azure Blob Trigger with Computer Vision and Text Analytics Integration

---

## **Overview**
This project demonstrates an Azure Function that integrates with Azure Blob Storage, Computer Vision, and Text Analytics services. The function is triggered whenever a new blob (file) is uploaded to a specific container in Azure Blob Storage. It processes the uploaded files, extracts insights using Azure Cognitive Services, and logs the results.

---

## **Features**
- **Blob Trigger**: Automatically triggers on file uploads to a specified Azure Blob Storage container.
- **Azure Computer Vision**: Extracts text from uploaded images.
- **Azure Text Analytics**: Analyzes the sentiment of the extracted text or any uploaded text document.
- **Scalable Architecture**: Leverages Azure Functions to ensure automatic scaling based on workload.

---

## **Prerequisites**
1. Azure subscription with the following resources:
   - Azure Blob Storage account and container.
   - Azure Cognitive Services (Computer Vision and Text Analytics).
2. **Local Development**:
   - Python 3.8 or later installed.
   - Azure Functions Core Tools installed.
   - VS Code with Azure Functions extension (recommended).
3. **Environment Variables**:
   - `AzureWebJobsStorage`: Blob Storage connection string.
   - `COMPUTER_VISION_ENDPOINT`: Endpoint for Computer Vision service.
   - `COMPUTER_VISION_KEY`: API key for Computer Vision service.
   - `LANGUAGE_SERVICE_ENDPOINT`: Endpoint for Text Analytics service.
   - `LANGUAGE_SERVICE_KEY`: API key for Text Analytics service.

---

## **Setup Instructions**

### **1. Clone the Repository**
```bash
git clone <repository-url>
cd <repository-folder>
```

### **2. Install Dependencies**
Ensure all required Python libraries are installed:
```bash
pip install -r requirements.txt
```

### **3. Update Configuration**
Add the following environment variables to your `local.settings.json`:
```json
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "<Your Blob Storage connection string>",
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "COMPUTER_VISION_ENDPOINT": "<Your Computer Vision endpoint>",
    "COMPUTER_VISION_KEY": "<Your Computer Vision API key>",
    "LANGUAGE_SERVICE_ENDPOINT": "<Your Text Analytics endpoint>",
    "LANGUAGE_SERVICE_KEY": "<Your Text Analytics API key>"
  }
}
```

### **4. Start the Function Locally**
Run the Azure Function locally:
```bash
func start
```

### **5. Test the Function**
1. Upload a file (image or text document) to the Blob Storage container.
2. Check the local logs to verify the function processed the file:
   - Logs should display extracted text and sentiment analysis results.

---

## **Deployment**
1. Deploy the function to Azure using the Azure Functions Core Tools:
   ```bash
   func azure functionapp publish <YourFunctionAppName>
   ```
2. Monitor the function in the Azure Portal under the **Log Stream** or **Monitor** sections.

---

## **Project Structure**
```
├── function_app.py       # Main function logic for Blob Trigger
├── function.json         # Blob Trigger configuration
├── local.settings.json   # Local environment configuration
├── requirements.txt      # Python dependencies
├── host.json             # Azure Functions host configuration
```

---

## **Key Features and Functionality**

### **Trigger Logic**
- The function automatically triggers when a blob is uploaded to a container.

### **Computer Vision Integration**
- Extracts text from images and logs the output.

### **Text Analytics Integration**
- Processes extracted or directly uploaded text to analyze sentiment and provides confidence scores.

---

## **Troubleshooting**

### **Common Errors**
1. **Module Not Found**:
   - Ensure all dependencies are installed via `pip install -r requirements.txt`.
2. **Invalid Hostname**:
   - Verify the environment variables for endpoint URLs are correctly formatted.
3. **Blob Trigger Not Firing**:
   - Confirm the container name in the function configuration matches the actual Blob Storage container.

### **Monitoring Logs**
- Use Azure Portal's **Log Stream** or Application Insights (if enabled) to monitor runtime logs.

---

## **Future Enhancements**
- Support for multiple file formats (PDF, CSV, etc.).
- Integration with additional Cognitive Services for extended capabilities.
- Storage of extracted insights in a database for further processing.

---

## **Contributing**
Feel free to submit issues, suggest improvements, or create pull requests to enhance this project. 😊

--- 
