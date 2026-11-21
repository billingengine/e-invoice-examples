# E-Rechnung Beispiele: XRechnung und ZUGFeRD

Beispieldateien für E-Rechnungen nach EN 16931 im Format XRechnung und ZUGFeRD / Factur-X:
XML-Dateien und PDFs mit eingebettetem XML, jeweils mit kurzer Erklärung. Alle Namen, Adressen,
IBANs und Nummern sind erfunden.

Die Dateien wurden mit [BillingEngine](https://www.billingengine.com/de) erzeugt und mit dem
Validator von BillingEngine geprüft (Schema, EN-16931-Regeln und XRechnung-Regeln für die
CII-Syntax, ohne Fehler). Sie eignen sich als Testdaten für eigene Software, zum Vergleichen mit
eigenen Dateien und zum Lernen, wie eine E-Rechnung aufgebaut ist.

Alle Dateien gibt es auch auf der Website, mit Erklärungen und häufigen Fragen:
[E-Rechnungsbeispiel](https://www.billingengine.com/de/examples/e-rechnungsbeispiel). Dazu fertig
ausgefüllte Rechnungen, Angebote, Quittungen und mehr: [Beispiele](https://www.billingengine.com/de/examples).

## Dateien

| Datei | Zeigt | Besonderheit |
| --- | --- | --- |
| [`01-standard-19-prozent`](examples/01-standard-19-prozent.xml) | Normale Rechnung, ein Steuersatz | XRechnung, mit Leitweg-ID als Käuferreferenz (`BuyerReference`). Auch als [PDF mit eingebettetem XML](examples/01-standard-19-prozent.pdf). |
| [`02-zwei-steuersaetze`](examples/02-zwei-steuersaetze.xml) | Positionen mit 19 % und 7 % | Zwei Steueraufschlüsselungen im Kopf |
| [`03-mit-rabatt`](examples/03-mit-rabatt.xml) | Rechnung mit Rabatt auf die Summe | Rabatt als Nachlass auf Dokumentebene (`AllowanceTotalAmount`) |
| [`04-kleinunternehmer-ohne-umsatzsteuer`](examples/04-kleinunternehmer-ohne-umsatzsteuer.xml) | Rechnung ohne Umsatzsteuer nach § 19 UStG | Steuerkategorie `E` mit Befreiungsgrund (`ExemptionReason`), keine USt-IdNr. des Verkäufers. Auch als [PDF](examples/04-kleinunternehmer-ohne-umsatzsteuer.pdf). |
| [`05-stornorechnung`](examples/05-stornorechnung.xml) | Stornorechnung zu Datei 05a | Dokumentart `381`, Verweis auf die stornierte Rechnung |
| [`05a-stornierte-originalrechnung`](examples/05a-stornierte-originalrechnung.xml) | Die Rechnung, die storniert wird | Gehört zu Datei 05 |
| [`06-zugferd-en16931-ohne-plz-ort`](examples/06-zugferd-en16931-ohne-plz-ort.xml) | Rechnung an einen Kunden ohne Postleitzahl und Ort | Nur das EN-16931-Profil, nicht XRechnung. Auch als [PDF](examples/06-zugferd-en16931-ohne-plz-ort.pdf). |

Alle Beispiele nutzen die CII-Syntax (Cross Industry Invoice). UBL ist nicht enthalten.

## Wichtige Felder

Pfade ohne Namensraum-Präfixe. Die Nummern in Klammern sind die Business Terms der EN 16931.

| Feld | Pfad | Beispiel |
| --- | --- | --- |
| Profil (BT-24) | `GuidelineSpecifiedDocumentContextParameter/ID` | `urn:cen.eu:en16931:2017#compliant#urn:xeinkauf.de:kosit:xrechnung_3.0` |
| Rechnungsnummer (BT-1) | `ExchangedDocument/ID` | `26-000001` |
| Dokumentart (BT-3) | `ExchangedDocument/TypeCode` | `380` Rechnung, `381` Stornorechnung (Gutschrift) |
| Käuferreferenz (BT-10) | `ApplicableHeaderTradeAgreement/BuyerReference` | Leitweg-ID bei Behörden |
| Umsatzsteuer gesamt (BT-110) | `SpecifiedTradeSettlementHeaderMonetarySummation/TaxTotalAmount` | `152.95` |
| Bruttosumme (BT-112) | `SpecifiedTradeSettlementHeaderMonetarySummation/GrandTotalAmount` | `957.95` |
| Zahlbetrag (BT-115) | `SpecifiedTradeSettlementHeaderMonetarySummation/DuePayableAmount` | `957.95` |
| Befreiungsgrund (BT-120) | `ApplicableTradeTax/ExemptionReason` | siehe Datei 04 |

Beträge stehen mit Punkt und zwei Nachkommastellen im XML, Datumsangaben als `YYYYMMDD`.

## Selbst prüfen

- Im Browser: [E-Rechnungsvalidator](https://www.billingengine.com/de/tools/e-rechnungsvalidator)
  (XML oder PDF hochladen) oder [E-Rechnungsviewer](https://www.billingengine.com/de/tools/e-rechnungsviewer)
  zum Lesen einer Datei.
- Offline: der [KoSIT-Validator](https://github.com/itplr-kosit/validator) mit der
  [XRechnung-Konfiguration](https://github.com/itplr-kosit/validator-configuration-xrechnung).

## Hinweise

- Die Dateien sind Beispiele, keine Rechtsberatung. Prüfen Sie Ihre eigenen Rechnungen vor dem
  Versand mit einem Validator und fragen Sie bei Zweifeln Ihre Steuerberatung.
- Die Leitweg-ID `04011000-1234512345-06` ist ein Platzhalter und gehört keiner Behörde.

## English

Sample German e-invoices (EN 16931, CII syntax) as XRechnung and ZUGFeRD / Factur-X: plain XML
files and PDFs with embedded XML, covering a standard invoice, two VAT rates, a discount, a small
business invoice without VAT (§ 19 UStG), a cancellation invoice and an invoice to a customer
without postal code and city. All data is fictional. The files were created with
[BillingEngine](https://www.billingengine.com/en) and checked with its validator (schema, EN 16931
and XRechnung rules, no errors). See the table above for what each file shows.

The files are also on the website, with explanations and frequently asked questions:
[e-invoice example](https://www.billingengine.com/en/examples/e-invoice-example). There are more
filled-in documents such as invoices, quotes and receipts under
[examples](https://www.billingengine.com/en/examples).

## Lizenz / License

MIT, siehe [LICENSE](LICENSE).
