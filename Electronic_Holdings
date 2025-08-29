import pandas as pd
from google.colab import drive
drive.mount('/content/drive/')
!ls
KBART = pd.read_table('/content/drive/<InsertFilepath>/Kbart.txt', header=0, delimiter='\t', low_memory=False)
column_names = list(KBART.columns.values)
print(column_names)
exclusions = ['AgEcon Search', 'American Physical Society Publications', 'American Phytopathological Society Journal Back Issues', 'Archive of African Journals', 'Asian Development Bank (ADB)', 'Association for Research in Vision and Ophthalmology', 'Books at JSTOR Evidence Based Acquisitions', 'Cairn Revues Free access Journals', 'Chronicling America: Historic American Newspapers', 'Ebook Central DDA Titles', 'Freely Accessible Science Journals', 'HathiTrust US Access with possible download restrictions', 'Hindawi Journals', 'Kanopy PDA US', 'Knowledge Unlatched', 'Knowledge Unlatched 2017', 'Knowledge Unlatched Round 2', 'Knowledge Unlatched Select 2016', 'KU Select 2016: Backlist Collection', 'KU Select 2016: Frontlist Collection', 'KU Select 2017: Backlist Collection', 'KU Select 2017: Frontlist Collection', 'KU Select 2017: Journal Collection', 'KU Select 2018: HSS Backlist Books', 'KU Select 2018: STEM Backlist Books', 'KU Select 2018: STEM Frontlist Books', 'Multidisciplinary Digital Publishing Institute', 'Persee journals', 'Public Library of Science', 'SORA journals', 'Wessex Institute of Technology Press', 'WVU Accademia Nazionale dei Lincei Publications', 'WVU Ebsco eJournals No-Proxy', 'WVU Free Full-Text Journals in Chemistry', 'WVU Free Medical Journals', 'WVU Freely Accessible Journals', 'Scopus*', 'Salem Press Online']
KBExclusions = KBART[~KBART['oclc_collection_name'].isin(exclusions)]
KBExclusions2 = KBExclusions[~KBExclusions['oclc_collection_name'].str.contains('Open', case=False, regex=False)]
ebooks = KBExclusions2.loc[(KBExclusions['coverage_depth'] == 'ebook')]
ebooks.head(n=50)
len(ebooks)
ebooksfromKBART_MMMDDYYYY_1_of_2 = ebooks.iloc[:1000000]
ebooksfromKBART_MMMDDYYYY_2_of_2 = ebooks.iloc[1000000:]
ebooksfromKBART_MMMDDYYYY_1_of_2.to_csv('/content/drive/<InsertFilepath>/ebooksfromKBART_MMMDDYYYY_1_of_2.txt', sep='\t', mode='a')
ebooksfromKBART_MMMDDYYYY_2_of_2.to_csv('/content/drive/<InsertFilepath>/ebooksfromKBART_MMMDDYYYY_2_of_2.txt', sep='\t', mode='a')
ejournals = KBExclusions2.loc[(KBExclusions['coverage_depth'] == 'fulltext')]
ejournals.to_csv('/content/drive/My Drive/<InsertFilepath>/ejournalsfromKBART_MMMDDYYYY_1_of_1.txt', sep='\t', mode='a')
