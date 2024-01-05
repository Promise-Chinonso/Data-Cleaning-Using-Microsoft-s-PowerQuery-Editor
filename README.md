### Data Cleaning: Inspecting and Wrangling the FIFA 21 Data Using PowerQuery
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/c39c8b18-0ee7-4a95-a64b-f875fd2f9fb1)

#### Background 
I organized a #datacleaningchallenge in the data-tech space alongside a fellow Data enthusiast in a bid to create an enabling environment to allow beginners, intermediates, and pro data analysts to flex their data cleaning skills. As the co-organizer, I was not left out as I also joined as a participant to transform the dataset provided for the challenge using Microsoft’s PowerQuery editor.

As you might already know, data cleaning and transformation is one of the core stages every data must go through before analysis. It ensures that the insights generated are accurate and not influenced by any inconsistencies, errors or dirtiness tied to the data.
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/5ab96c18-854d-46de-85a6-cb72ce68110f)

#### Specific objectives of the data cleaning process
• Ensure that all the columns have the correct data type
• Numerical columns should be in a format suitable for further calculations and analysis

Meeting these two objectives requires that a good number of factors be checkmated, some of which are; the presence of null entries, empty rows, special characters, irregularities, inconsistent naming conventions etc. 

#### About the data
The dataset used for this challenge is the FIFA 21 data. It was sourced from Kaggle. The dataset was obtained in its raw state after web scrapping from sofifa.com. It contains the details of football players alongside their performance, updated up till 2021. It is worth noting that there are 18979 rows and 77 columns present in the FIFA 21 data. 

#### Data Discovery and Cleaning
The dataset was imported into the Powerquery editor, and loaded for transformation.

The dataset from my observation had numerous issues that i fixed during the cleaning process. Follow me as I walk you through the process of transforming this data from its messy state to a clean state making it ready for analysis. 

The 'ID' column has unique numbers assigned to every player
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/985e26cf-3ad3-46aa-a65f-9297fc43cf2d)

The 'Name’, 'LongName' and 'PlayerURL' columns all had information relating to players' names. The Name column has names written in the format, 'C. Ronaldo’, the LongName column had the initials, first name, middle name and last name of players in one place while the PlayerURL column had the players' full names embedded within the URL.
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/d2365625-3781-467c-ae5d-6ef27f4e13ea)

_Using the Name column as the only column bearing players' names was not a good idea considering the fact that the first names of the players were shortened to one alphabet. Deciding to settle with the LongName column was not a great idea either since the names in that column contained special characters that would have been more challenging to get rid of. 
I resorted to extracting the full names of the players from the PlayerURL column. 
Process: the column was split using the '/' and '-' delimiters at each occurrence. This process split the column into over 7 columns. The columns bearing the players' names were retained and merged into one column and each letter was capitalized._

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/1c887666-fd93-4e79-a024-162939401e6f)

PhotoURL' and 'PlayerURL' columns contained links that can be used to access the image and details of all the players represented in the data. These columns were removed from the data.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/4f52d4fa-6f9e-485a-9635-23dda260b118)

Nationality, Age and Club columns had no missing entries, null values, or data type issues. I considered them okay and moved to the next columns.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/603c4663-da2e-4e49-8326-0af32cea91cf)

The 'Contract' column had inconsistent values and the wrong data type. The column has 3 categories of values in the format, '23rd July 2020 on loan’, 'Free' and '2018 ~ 2024’.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/5a713e71-fd72-41a1-8edd-30d44cc4e6c1)

_To tackle this issue, I had the column split using the space delimiter to give two columns containing the Contract start date and the Contract end date. 
Process: I split the column using 'space' as the delimiter. Over 4 columns were created, got rid of all except the columns with Contract start and Contract end details. The columns were renamed, and the entries which were not in year format were replaced with 'Null’. This was done to allow the conversion of these two new columns to date types and also nullify records of players on 'Loan' and 'Free' from the Contracts column._

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/f8527bff-7db3-41ca-8e98-1dd0d182ce63)

'Positions' column was removed because there is another column bearing the 'Best_Position' of each player. The 'Positions' column had the details in the 'Best_Position' column in addition to the extra positions for players that had more than one position.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/a0d117ea-8a2a-4680-bff9-272f81ee142b)

'Joined' column was filtered to see if there are inconsistencies in the data keyed into it. The column has consistent data and the correct data type (date).
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/1b2204fd-fdc0-4212-904a-f701b7dc48be)

'Loan_date_end' has 95% empty rows. This is understandable as the total number of players on loan accounts for only 5% of the entire data. Only players on loan have values in this column.
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/b92c772f-38f7-4e98-9f1f-decd265b12a7)

_To tackle the problem with the empty spaces, I replaced all empty spaces with 'Null’._

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/17811b0b-f4d2-4fef-8276-e2e1cc560001)

A good number of the fields in the table had no issues with their values. The data types were checkmated, and changes were made for some that had wrong data types and inconsistent column names.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/817c0d82-bcd9-4f41-83a1-ab639f000c7a)

'Weak_foot’, 'Skill_moves’, and 'International_reputation' columns all contain ratings on a scale of 1-5. The values in these columns had the special character '☆' in front and the data type was text.
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/b43d6184-eca0-4e46-bf60-ccbab3c79745)

_I replaced the special character with space, wrote the column names in full and then converted the column data types from text to whole number_

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/c6859449-ba2e-4c44-93ba-2bc235204c21)

'Height' and 'Weight' columns had inconsistencies in the units attached to their values.
- For the 'Height' column, the entries were in the format, '110cm’, 5’2" (feet & inches).

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/13286822-1161-47f5-83c2-3aad80b61d0e)

- For the 'Weight' column, entries were in the format, '65kg’, '112lbs’.

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/b3ae922b-5281-4cef-8c1a-e3b11dcf9d9c)

_The data type was stored as text. To convert the data type to a whole number, I had to first get rid of the suffixes after each value in both columns. To achieve this goal, the values in the height column in feets&inches were converted to 'cm' and for the weight, the values in lbs were converted to 'kg' before removing the unwanted suffixes._

  - The interconversions were possible using the formula below for height column conversion and weight column conversion.

For height:  `if Text.EndsWith([Height], "cm") then Number.FromText(Text.RemoveSuffix([Height], "cm")) else let feet = Text.BeforeDelimiter([Height], "’"), inches = Text.BeforeDelimiter(Text.AfterDelimiter([Height], "’"), """"), totalInches = (Number.FromText(feet) * 12) + Number.FromText(inches), cm = totalInches * 2.54 in cm`

For weight: `if Text.EndsWith([Weight], "lbs") then Number.FromText(Text.Start([Weight], Text.Length([Weight]) - 3)) * 0.45359237
else Number.FromText(Text.Start([Weight], Text.Length([Weight]) - 2))`

'Potential_rating’, 'Best_overall_rating' and 'Overall_rating' columns had values in the range of 1-99.
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/ac525dc1-cce6-4d68-b67e-523c29e9f63d)

_Further research about these fields showed that it is best for the values to be represented in percentages. To achieve this, these columns were first converted to integer data types, divided by hundred, and then subsequently converted to the percentage data type which multiplied all the values by a factor of 100._
    
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/8e8e42a2-d1ba-4924-81fb-0c8687b32ff1)

'Hits' column was stored as text data type but contained numbers (whole number and decimal number types) with the 'K' suffixes. For context, values like 1600 were stored as 1.6K.
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/3923e650-f7a5-46b7-8521-61dd4f1db03e)

_To get these values in numerical format, I created a conditional column which gave an output of 1000 for every row that has 'K' in the 'Hits' column and returned 1 if otherwise. After creating the conditional column, the 'K' in the 'Hits' column was replaced with space and the data type was converted to an integer. The final step involved creating a custom column whose formula was a multiplication of values in the conditional column and that in the Hits column. The custom column was renamed to 'Hits’, and the conditional column and original 'Hits' column were removed._
    
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/a605e522-df98-4a07-80dc-ff84e67f05b5)

'Value’, 'Wage' and 'Release_clause' columns had data type issues and values with suffixes in front. These columns had suffixes 'M' for millions, 'K' for thousands and '€' for euro (currency).
  
![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/89a1e69e-f0d3-4af7-bbe0-9309839312ed)

_To normalize the values(whole number and decimal) in these columns and get rid of the suffixes, a conditional column was created as in the 'Hits' column. The suffixes were replaced with space, data types were converted, and the custom column was created for the multiplication of values in these original columns and the values in the conditional columns. The new columns containing the normalized values were converted to whole number data types and renamed._

![image](https://github.com/Promise-Chinonso/Data-Cleaning-Using-Microsoft-s-PowerQuery-Editor/assets/104436236/148e14f9-dd39-4a61-a4f0-702e0cae9d66)

#### Conclusion
Cleaning the FIFA 21 data was a bit challenging. Despite the challenges encountered, the messy dataset was transformed into a state that renders it ready for use in analysis.




