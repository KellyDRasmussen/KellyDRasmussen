Here is your cleaned-up markup code for your GitHub page:

```markdown
### Tutorial: Cleaning and Processing Product Data

We need this by the end of today (Friday) so that we can use your code for the next part.

Steps 1-4 are on this video: [Tutorial Video](https://www.awesomescreenshot.com/video/27989529?key=bda2677a21a2a9177cac488092005fef)

#### Step 1: Filter Products on the Website
1. Go to [Arla Pro's website](https://www.arlapro.com/da/produkter/).
2. Filter the products to display only "Ost" and "Unika" categories.

#### Step 2: Copy Product Names to Google Sheets
1. Select and copy the body of the website that contains all the product names.
2. Open Google Sheets.
3. In the first cell of the first column (A1), type `Product`.
4. Below `Product`, paste the copied content as values only.
   - To paste as values, use `Ctrl + Shift + V` (Windows) or `Cmd + Shift + V` (Mac).

#### Step 3: Download the Data as CSV
1. Click on `File` in the top-left corner.
2. Select `Download` and then `Comma-separated values (.csv, current sheet)`.
3. Save the file with a clear filename, for example, `unika_products.csv`.

#### Step 4: Upload the CSV File to Google Drive
1. Open Google Drive in your browser.
2. Navigate to the folder `team cheese/data/raw`.
3. Upload the downloaded `unika_products.csv` file to this folder.

#### Step 5: Process the CSV File Using Pandas

Now, let's move on to the coding part to clean and process the CSV file. We'll go step-by-step to make it easy to follow.

##### Step 5.1: Mount Google Drive
1. Open a google colab file
2. Mount your Google Drive using the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

   </details>

##### Step 5.2: Load the Libraries
Import the necessary libraries. Type the following code and run it:
   <details>
   <summary>Click to expand code</summary>

   ```python
   import pandas as pd
   import numpy as np
   ```

   </details>

##### Step 5.3: Load the CSV File
Load the CSV file into a pandas DataFrame. Adjust the file path if necessary:
   <details>
   <summary>Click to expand code</summary>

   ```python
   file_path = '/content/drive/My Drive/team cheese/data/raw/unika_products.csv'
   df = pd.read_csv(file_path)
   ```

   </details>

##### Step 5.4: Delete "KØB NU" and "UNIKA"
Replace the values "KØB NU" and "UNIKA" with `NaN`. Run the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   values_to_delete = ['UNIKA', 'KØB NU']
   df['Product'] = df['Product'].replace(values_to_delete, np.nan)
   ```

   </details>

##### Step 5.5: Delete Copies (Remove Duplicates)
Keep only the first occurrence of each product name and replace duplicates with `NaN`. Use the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   def remove_duplicates(column):
       seen = set()
       return [x if x not in seen and not seen.add(x) else np.nan for x in column]

   df['Product'] = remove_duplicates(df['Product'])
   ```

   </details>

##### Step 5.6: Delete Rows with `NaN`
Remove rows that contain `NaN` values. Run this code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   df = df.dropna()
   ```

   </details>

##### Step 5.7: Reindex the DataFrame
Reset the index of the DataFrame to ensure it starts from 0. Use the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   df = df.reset_index(drop=True)
   ```

   </details>

##### Step 5.8: Save the Cleaned Data
Save the cleaned DataFrame back to a CSV file. Adjust the file path if necessary:
   <details>
   <summary>Click to expand code</summary>

   ```python
   cleaned_file_path = '/content

```markdown
   /drive/My Drive/team cheese/data/processed/unika_products_cleaned.csv'
   df.to_csv(cleaned_file_path, index=False)
   ```

   </details>

### Tutorial: Cleaning and Processing Castello Product Data

We need this by the end of today (Friday) so that we can use your code for the next part.

#### Step 1: Filter Castello Products on the Website
1. Go to [Arla Pro's website](https://www.arlapro.com/da/produkter/).
2. Filter the products to display only "Ost" and "Castello" categories.

#### Step 2: Copy Product Names to Google Sheets
1. Select and copy the body of the website that contains all the product names.
2. Open Google Sheets.
3. In the first cell of the first column (A1), type `Product`.
4. Below `Product`, paste the copied content as values only.
   - To paste as values, use `Ctrl + Shift + V` (Windows) or `Cmd + Shift + V` (Mac).

#### Step 3: Download the Data as CSV
1. Click on `File` in the top-left corner.
2. Select `Download` and then `Comma-separated values (.csv, current sheet)`.
3. Download the file with a clear filename, for example, `castello_products.csv`.

#### Step 4: Upload the CSV File to Google Drive
1. Open Google Drive in your browser.
2. Navigate to the folder `team cheese/data/raw`.
3. Upload the downloaded `castello_products.csv` file to this folder.

#### Step 5: Process the CSV File Using Pandas

Now, let's move on to the coding part to clean and process the CSV file. We'll go step-by-step.

##### Step 5.1: Mount Google Drive
1. Open a google colab file
2. Mount your Google Drive using the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

   </details>

##### Step 5.2: Load the Libraries
Import the necessary libraries. Type the following code and run it:
   <details>
   <summary>Click to expand code</summary>

   ```python
   import pandas as pd
   import numpy as np
   ```

   </details>

##### Step 5.3: Load the CSV File
Load the CSV file into a pandas DataFrame. Adjust the file path if necessary:
   <details>
   <summary>Click to expand code</summary>

   ```python
   file_path = '/content/drive/My Drive/team cheese/data/raw/castello_products.csv'
   df = pd.read_csv(file_path)
   ```

   </details>

##### Step 5.4: Delete "KØB NU" and "UNIKA"
Replace the values "KØB NU" and "UNIKA" with `NaN`. Run the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   values_to_delete = ['UNIKA', 'KØB NU']
   df['Product'] = df['Product'].replace(values_to_delete, np.nan)
   ```

   </details>

##### Step 5.5: Delete Copies (Remove Duplicates)
Keep only the first occurrence of each product name and replace duplicates with `NaN`. Use the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   def remove_duplicates(column):
       seen = set()
       return [x if x not in seen and not seen.add(x) else np.nan for x in column]

   df['Product'] = remove_duplicates(df['Product'])
   ```

   </details>

##### Step 5.6: Delete Rows with `NaN`
Remove rows that contain `NaN` values. Run this code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   df = df.dropna()
   ```

   </details>

##### Step 5.7: Reindex the DataFrame
Reset the index of the DataFrame to ensure it starts from 0. Use the following code:
   <details>
   <summary>Click to expand code</summary>

   ```python
   df = df.reset_index(drop=True)
   ```

   </details>

##### Step 5.8: Save the Cleaned Data
Save the cleaned DataFrame back to a CSV file. Adjust the file path if necessary:
   <details>
   <summary>Click to expand code</summary>

   ```python
   cleaned_file_path = '/content/drive/My Drive/team cheese/data/processed/castello_products_cleaned.csv'
   df.to_csv(cleaned_file_path, index=False)
   ```

   </details>
```

This version should be properly formatted for your GitHub page.
