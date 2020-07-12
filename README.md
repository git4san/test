> # Steps to follow for LinkedIn Scrap

> ## Create a virtualenv

```diff
# $ python3 -m venv linkedin-scrap
# $ source linkedin-scrap/bin/activate
```

> ## Install the initial requirements
```diff
# $ cd scrap-linkedin/
# $ pip install -r requirements.txt
# $ python setup.py install <!--scrapeli will get installed here-->
```

> ## Get and Set the LI_AT 
### to make selenium browser as like an actual user. Need to add the li_at cookie to the selenium session
```diff
! Step 1: Navigate to www.linkedin.com in Chrome. better to have the stable version 83.0.4103.39
! Step 2: Login with your linkedin id and password
! Step 3: Right click on the chrome browser and select "inspect element"
! Step 4: You may see a set of tabs such as Elements, Console, Sources, Network etc at the top of the inspect  window. Select the Application tab. 
! Step 5: Select and copy the value of "li_at"
! Step 6: Set the LI_AT environment varibale. 
```
```diff
# $ export LI_AT=THE_COPIED_LI_VALUE
```
```diff
! Press Enter.
```

> ## Now set your chromedriver into the path. 
```diff
! Step 1: Check your chrome path
# $ which google-chorme // it may be in /usr/bin/google-chrome
! Step 2: Now set the chromedriver
# $ sudo apt-get install chromium-browser
! Step 3: Download the chromedriver version. Get the same version 83.0.4103.39
+ http://chromedriver.storage.googleapis.com/index.html
+ Get the chromedriver_linux64.zip
! Step 4: Unzip the chromedriver.zip
! Step 5: Move the file to /usr/bin/ directory 
# $ sudo mv chromedriver /usr/bin/
# $ cd /usr/bin/
# $ chmod a+x chromedriver
# $ export PATH=$PATH:/usr/binchrome-driver
```

> ## Run scrapeli
```diff
# $ scrapeli --user=user_profile_name 
- or
# $ scrapeli --user=user_profile_name -o profile_scrapped_result.json
- or 
# $ scrapeli --url=https://www.linkedin.com/in/user_profile_name/

- You may also provide attribute
+--attribute "-a": choice: phone. (choose from personal_info, experiences, skills, accomplishments, interests)
# $ scrapeli --user=user_profile_name -a personal_info 

- The above command (scrapeli --user=user_profile_name) will scrap all the details of a inkedin profile provided. Details such as:

+ 1. personal_info (name, company, school, headline, followers, summary, websites, email, phone, connected, current_company_link, image)
+ 2. skills
+ 3. experiences (volunteering, jobs, education)
+ 4. interests
+ 5. accomplishments (publications, cerfifications, patents, courses, projects, honors, test scores, languages, organizations)

> ## If you want to scrap a company profile, then
# $ cd examples/
# $ python companies-to-csv.py // result will be saved as out.csv
- or 
# $ cd scrape_linkedin/
# $ python company.py
- The above command will scrap the details of the company name provided inside the companies-to-csv.py. You may add any number of company names inside the program companies-to-csv to scrap the details
- If any error such as ModuleNotFoundError: No module named 'pandas', then install pandas
# $ pip install pandas

- The above command (python companies-to-csv.py) will scrap the details of company name provided, such as:
+ 1. Overview (name, company_size, websir, industyr, headquarters, type, founded, specialities, num_of_employees, image and company_name)

> ## If you want to scrap many companies (may be more than 15, then better to run parallel.py. Inside the program, you may mention any number of company names to scrap and it will produce a json file (companies.json) as output)
# $ cd scrape_linkedin/
# $ python parallel.py
```
