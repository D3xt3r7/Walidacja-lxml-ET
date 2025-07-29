JPK_V7M XML Validation and Parsing
Overview
This project provides a Python script to validate and parse JPK_V7M XML files, which are used in Poland for VAT reporting. The script uses the lxml library to validate XML files against an XSD schema and extract key information such as header details, entity information, and sales records.
Features

XML Validation: Validates JPK_V7M XML files against the provided XSD schema.
Data Parsing: Extracts and displays key information from the JPK_V7M file, including:
Header details (form code, variant, creation date).
Entity details (NIP, full name).
Sales records (line number, contractor details, net and VAT amounts).


Error Handling: Provides detailed error messages for XML syntax issues or validation failures.

Prerequisites

Python 3.x
lxml library (pip install lxml)
JPK_V7M XML file and corresponding XSD schema file

Usage

Ensure the XML file (jpk_v7m.xml) and XSD schema file (JPK_V7M_1_0.xsd) are in the project directory or update the file paths in the script.
Run the script:python jpk_validation.py


The script will:
Validate the XML file against the XSD schema.
If valid, parse and display key information from the XML file.
If invalid, display validation errors.



File Structure

jpk_validation.py: Main Python script for XML validation and parsing.
jpk_v7m.xml: Sample JPK_V7M XML file (example structure provided).
JPK_V7M_1_0.xsd: XSD schema file for JPK_V7M validation (not included in this repository; must be obtained separately).

Example XML Structure
The JPK_V7M XML file follows this structure:
<?xml version="1.0" encoding="UTF-8"?>
<JPK xmlns="http://jpk.mf.gov.pl/wzor/2020/10/01/10011/" xmlns:etd="http://crd.gov.pl/xml/schematy/dziedzinowe/mf/2020/06/25/eD/DefinicjeTypy/">
  <Naglowek>
    <KodFormularza>JPK_V7M</KodFormularza>
    <WariantFormularza>1</WariantFormularza>
    <DataWytworzeniaJPK>2023-10-01T12:00:00</DataWytworzeniaJPK>
  </Naglowek>
  <Podmiot1>
    <IdentyfikatorPodmiotu>
      <etd:NIP>1234567890</etd:NIP>
      <etd:PelnaNazwa>Firma Testowa</etd:PelnaNazwa>
    </IdentyfikatorPodmiotu>
  </Podmiot1>
  <SprzedazWiersz>
    <LpSprzedazy>1</LpSprzedazy>
    <NrKontrahenta>9876543210</NrKontrahenta>
    <NazwaKontrahenta>Kontrahent SA</NazwaKontrahenta>
    <K_19>1000.00</K_19>
    <K_20>230.00</K_20>
  </SprzedazWiersz>
</JPK>

Output Example
Running the script on a valid JPK_V7M XML file produces output like:
Plik jpk_v7m.xml jest poprawny względem schematu XSD.
Nagłówek JPK:
  Kod formularza: JPK_V7M
  Wariant formularza: 1
  Data wytworzenia: 2023-10-01T12:00:00
Podmiot:
  NIP: 1234567890
  Nazwa: Firma Testowa
Liczba wierszy sprzedaży: 1
Wiersz sprzedaży 1:
  LP: 1
  Nr kontrahenta: 9876543210
  Nazwa kontrahenta: Kontrahent SA
  Netto (K_19): 1000.00
  VAT (K_20): 230.00

Notes

Ensure the XSD schema file matches the JPK_V7M version used in the XML file.
The script assumes the XML file follows the namespace definitions provided in the example.
For production use, consider adding additional error handling and logging.

Repository
GitHub Repository
