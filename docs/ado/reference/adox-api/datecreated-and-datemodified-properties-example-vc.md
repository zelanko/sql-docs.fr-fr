---
title: DateCreated et DateModified, exemples de propriétés (VC ++) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateCreated property [ADOX], VC++ example
- DateModified property [ADOX], VC++ example
ms.assetid: b964beee-83c7-4f91-8255-3ba864c9adfd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 07fe23064173ba6e5c64294f9ea89615909cb10f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966606"
---
# <a name="datecreated-and-datemodified-properties-example-vc"></a>DateCreated et DateModified, exemples de propriétés (VC++)
Cet exemple montre la [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propriétés en ajoutant une nouvelle [colonne](../../../ado/reference/adox-api/column-object-adox.md) à un existant [Table](../../../ado/reference/adox-api/table-object-adox.md) et par Création d’un nouveau **Table**. La procédure DateOutput est requise pour exécuter cet exemple.  
  
```  
// BeginDateCreatedCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void DateCreatedX();  
void DateOutPut(_bstr_t strTemp, _TablePtr tblTemp);  
  
int main() {  
    if ( FAILED(::CoInitialize(NULL) ) )  
        return -1;  
    DateCreatedX();  
    ::CoUninitialize();  
}  
  
void DateCreatedX() {  
    HRESULT hr = S_OK;  
  
    // Define ADOX object pointers, initialize pointers. These are in ADODB  namespace.  
    _CatalogPtr m_pCatalog = NULL;  
    _TablePtr m_pTblEmployees = NULL;  
    _TablePtr m_pTblNew = NULL;  
  
    // Set ActiveConnection of Catalog to this string  
    _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source= 'c:\\Northwind.mdb';");  
  
    try {  
        TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
  
        // Connect the catalog.  
        m_pCatalog->PutActiveConnection(strCnn);  
        m_pTblEmployees = m_pCatalog->Tables->GetItem("Employees");  
  
        // Print current information about the Employees table.  
        DateOutPut((_bstr_t)"Current properties", m_pTblEmployees);  
  
        // Create and append column to the Employees table.  
        m_pTblEmployees->Columns->Append("NewColumn", adInteger,0);  
        m_pCatalog->Tables->Refresh();  
  
        // Print new information about the Employees table.  
        DateOutPut((_bstr_t)"After creating a new column", m_pTblEmployees);  
  
        // Delete new column because this is a demonstration.  
        m_pTblEmployees->Columns->Delete("NewColumn");  
  
        // Create and append new Table object to the Northwind database.  
        TESTHR(hr = m_pTblNew.CreateInstance(__uuidof(Table)));  
  
        m_pTblNew->Name = "NewTable";  
        m_pTblNew->Columns->Append("NewColumn", adInteger,0);  
        m_pCatalog->Tables->Append(_variant_t((IDispatch*)m_pTblNew));  
        m_pCatalog->Tables->Refresh();  
  
        // Print information about the new Table object.  
        DateOutPut((_bstr_t)"After creating a new table", m_pCatalog->Tables->GetItem("NewTable"));  
  
        // Delete new Table object because this is a demonstration.  
        m_pCatalog->Tables->Delete(m_pTblNew->Name);  
    }  
  
    catch(_com_error &e) {  
        // Notify the user of errors if any.  
        _bstr_t bstrSource(e.Source());  
        _bstr_t bstrDescription(e.Description());  
  
        printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
    }  
  
    catch(...) {  
        cout << "Error occured in include files...." << endl;  
    }  
}  
  
void DateOutPut(_bstr_t strTemp , _TablePtr tblTemp) {  
    // Print DateCreated and DateModified information about specified Table object.  
    cout << strTemp << endl;  
    cout << "    Table: " << tblTemp->GetName() << endl;  
    cout << "        DateCreated = " << (_bstr_t)tblTemp->GetDateCreated() << endl;  
    cout << "        DateModified = " << (_bstr_t)tblTemp->GetDateModified() << endl;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [DateCreated, propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)   
 [DateModified, propriété (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)   
 [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
