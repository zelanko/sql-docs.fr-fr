---
title: Supprimer une Source de données (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff882caf0ce5d9ef7d2e9f059daed89ed4b50d82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126102"
---
# <a name="delete-a-data-source-odbc"></a>Supprimer une source de données (ODBC)
  Vous pouvez supprimer une source de données à l’aide de l’administrateur ODBC, par programmation (à l’aide de [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), ou en supprimant un fichier (si un nom de source de données de fichier).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Pour supprimer une source de données à l'aide de l'Administrateur ODBC  
  
1.  Dans **le panneau de configuration**, ouvrez **outils d’administration**, puis double-cliquez sur **Sources de données (ODBC)** . Vous pouvez également exécuter odbcad32.exe à partir de l'invite de commandes.  
  
2.  Cliquez sur le **DSN utilisateur**, **DSN système**, ou **fichier DSN** onglet.  
  
3.  Cliquez sur la source de données à supprimer.  
  
4.  Cliquez sur **supprimer**, puis confirmez la suppression.  
  
## <a name="example"></a>Exemple  
 Pour supprimer par programmation une source de données, appelez [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) en utilisant ODBC_REMOVE_DSN ou ODBC_REMOVE_SYS_DSN comme deuxième paramètre.  
  
 L'exemple suivant vous montre comment supprimer une source de données par programme.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques des procédures relatives à la configuration du pilote ODBC SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
