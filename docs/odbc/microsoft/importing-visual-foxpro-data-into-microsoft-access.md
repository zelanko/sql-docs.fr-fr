---
title: "L’importation de données Visual FoxPro dans Microsoft Access | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6bdf35fb9c9b7b4688aa7f5bf4173b2a6a9eefb5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>L’importation de données Visual FoxPro dans Microsoft Access
Vous pouvez importer des données stockées dans une base de données Visual FoxPro dans une base de données Microsoft Access à l’aide de l’option d’importation.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Pour importer des données Visual FoxPro dans une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Dans le menu fichier, choisissez que puis importer des données externes.  
  
3.  Dans la boîte de dialogue, sélectionnez les bases de données ODBC dans la liste de type de fichiers.  
  
4.  Dans la boîte de dialogue de Sources de données SQL, sélectionnez la source de données Visual FoxPro qui se connecte aux données FoxPro que vous souhaitez interroger et cliquez sur OK.  
  
5.  Dans la boîte de dialogue Importer des objets, sélectionnez un ou plusieurs tables à importer, cliquez sur OK. Les noms des tables Visual FoxPro que vous avez importé sont affichent dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour manipuler les données dans les tables Visual FoxPro importées. Les données que vous importez seront un instantané des données stockées dans Visual FoxPro ; modifications apportées aux données importées ne sont pas renvoyées à la source de données Visual FoxPro.  
  
 Si vous souhaitez que les modifications que vous apportez dans Microsoft Access pour modifier les données sur la source de données Visual FoxPro, consultez [exécution d’une requête et de mise à jour des données à partir de Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
