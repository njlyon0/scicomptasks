# Facilitating Pre-Morpho Wrangling

**"MainScript.R"**

- 

**"WriteUniqueFieldValues.R"**

- 




https://old.dataone.org/software-tools/morpho

## Purpose (as defined by original author):
Morpho has several major limitations with respect to user- friendliness. Many applications—Morpho and R included—will read in junk “columns” if any column outside of the data has any kind of user input. This includes white space. It is often hard to spot these columns until they are read into an application. I like to use Morpho’s Data Wizard’s automatic data entry feature when inputting new data tables into a data package. The problem is that Morpho will force you to input metadata for these junk columns—I often have up to 20 of these at a time—or else quit the process and start over after deleting the junk columns. This can hugely increase the time you have to spend in Morpho, and nobody wants that.
  
  Another issue with Morpho is that Morpho can’t parse really large datasets. Normally the wizard will identify unique values within a data field (i.e. a column in a .csv file, in my case), but failing to parse the data means that it won’t identify every unique value. For certain data types, you want to define your field’s values. There’s no way to look up the unparsed values in Morpho. Related to this is trying to determine the type of any numeric data you have (whole, natural, integer, or real). You want to be able to sort all of these values to see whether your data includes zeros, negative numbers, and/or fractions 	and decimals. If the data isn’t parsed fully, there’s no way to know for sure. 
  
  Finally, the way Morpho sorts data isn’t helpful for determining whether you have any missing values and what their code may be (“NA”, a blank cell/empty string, etc.). Running these scripts prior to using Morpho will allow you to more easily identify junk columns (see “MainScript.R Instructions”, above), to identify the type of any numeric data, and to identify what kinds of codes in your data indicate missing values.





Scripts:
  
  MainScript.R:
  
    The script with which users should interact. Sources the second script,
    WriteUniqueFieldValues.R.

  WriteUniqueFieldValues.R:
    
    Loads the magrittr package and defines the function that MainScript.R
    calls. The only reason to interact with this script is in the case of
    errors, likely due to three possible problems: non-Mac platforms for
    which this script was not tested, older versions of R (I used v3.3.1),
    or a different version of the magrittr package (I use v1.5).

MainScript.R Instructions:
  
  1. Change the path variables within the section entitled “User-dependent
  variables”. Make sure to use absolute paths, as specified in the comments in
  this section. Omit the trailing separator (“/” for Mac OS X and “\\” for
  Windows). Surround the path with quotation marks. For example:
  
  “/Users/justin/Desktop/MorphoScript”

  2. Choose whether to specify a value for custom_string_for_missing_values,
  which designates any user- defined values for missing data. Otherwise,
  ignore the variable. For example, if my .csv file indicates missing data by
  “Unknown” (without the quotes), the value of this variable would be
  “Unknown” (with the quotes).

  3. Source MainScript.R. 

  4. Look for files named after your dataset’s field names in the directory
  you specified as the value of variable “write_dir”. Any junk “columns” will
  be named “X”, “X.1”, X.2”, and so on. If your data is organized with
  variables as column headers and subsequent rows representing values for each
  variable, and if your data columns are contiguous, then “X” represents the
  first column after your last legitimate data column.

  5. Open your .csv file in Excel. Clear the contents of any junk “columns”
  you observe.

Purpose of scripts:
  
  
  