# **AI News & Sentiment Analyzer**

This is a single-file, browser-based web application that provides a powerful tool for monitoring and analyzing financial news. It fetches the latest business articles from various sources, uses a generative AI model to determine the sentiment (Positive, Negative, or Neutral) and identify the primary company mentioned in each headline, and can optionally send a summary of the findings as a push notification to your mobile device.

## **Features**

* **Multi-Source News Aggregation**: Pulls articles from top financial news outlets like Bloomberg, Reuters, The Wall Street Journal, and more.  
* **AI-Powered Analysis**: Leverages the Google Gemini API to perform sophisticated sentiment analysis and named entity recognition (company identification) on each article.  
* **Customizable Dashboard**: Users can easily select which news sources to include in their query.  
* **Intelligent Filtering**: A toggle switch allows users to hide articles where the AI could not identify a specific company, focusing the results on actionable information.  
* **Push Notifications**: Integrated with Pushover to send real-time, summarized reports directly to your phone. This feature can be toggled on or off.  
* **Modern & Responsive UI**: Built with Tailwind CSS for a clean, modern, and responsive user experience that works on any device.  
* **Zero Backend Required**: The entire application runs in the browser. No server-side code, databases, or complex setup needed.

## **How It Works**

The application operates in a simple, sequential flow, all handled by client-side JavaScript:

1. **Configuration**: The user enters their private API keys for NewsAPI (for fetching articles), Google Gemini (for AI analysis), and Pushover (for notifications). These keys are stored only for the current session and are not saved or transmitted anywhere else.  
2. **Fetch Articles**: When the user clicks the main button, the app constructs a query to the **NewsAPI**. It specifically searches for business-related keywords (like `stocks`, `market`, `earnings`) from the user-selected sources. To bypass the browser restrictions of the free NewsAPI plan, the request is routed through a public CORS proxy.  
3. **Analyze Concurrently**: Once the articles are received, the application sends the title and description of each article to the **Google Gemini API** in parallel for maximum efficiency. A carefully crafted prompt instructs the AI to return a JSON object containing the `sentiment` and the identified `company`.  
4. **Display Results**: The analyzed articles are immediately rendered on the page. Each article is displayed as a card showing the headline, source, identified company, and a colored dot representing the sentiment.  
5. **Filter & Notify**: The user can toggle the filter to hide articles where the company was not identified ('N/A'). If enabled, a formatted summary of the top 5 articles is sent to the **Pushover API**, which then delivers the push notification.

## **How to Use**

To run this application, you only need a web browser.

1. **Save the Code**: Save the `index.html` file to your local computer.  
2. **Get API Keys**: You will need to get three sets of API keys from the following services:  
   * **NewsAPI**: [Sign up for a free key at newsapi.org](https://newsapi.org/).  
   * **Google Gemini**: [Get a free key from Google AI Studio](https://aistudio.google.com/). You may need to enable the "Generative Language API" in your Google Cloud project.  
   * **Pushover**: [Register at pushover.net](https://pushover.net/). You will need your **User Key** (from your dashboard) and an **API Token** (by creating a new "Application").  
3. **Open the App**: Open the `index.html` file in your web browser (e.g., Chrome, Firefox, Edge).  
4. **Enter Keys**: Paste your API keys into the respective fields in the "Configuration" section.  
5. **Run**: Select your desired news sources, toggle your notification and filter preferences, and click the "Fetch, Analyze & Notify" button.

## **Technologies Used**

* **HTML5**  
* **Tailwind CSS**: For all styling and UI components.  
* **JavaScript (ES6+)**: For all application logic, including API calls and DOM manipulation.  
* **NewsAPI**: For aggregating news articles.  
* **Google Gemini API**: For sentiment analysis and entity recognition.  
* **Pushover API**: For sending push notifications.

