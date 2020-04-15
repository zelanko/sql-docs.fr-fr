---
title: Importation de données Visuelles FoxPro dans Microsoft Access (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90ac16bbdbaf7f4dd29e14e66cf5b9dc666057f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302444"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importation de données Visual FoxPro dans Microsoft Access
Vous pouvez importer des données stockées dans une base de données Visual FoxPro dans une base de données Microsoft Access à l’aide de l’option Importation.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Pour importer des données Visual FoxPro dans une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Dans le menu Fichier, choisissez Get External Data puis Import.  
  
3.  Dans la boîte de dialogue Import, sélectionnez les bases de données ODBC dans les fichiers de la liste de type.  
  
4.  Dans la boîte de dialogue SQL Data Sources, sélectionnez la source de données Visual FoxPro qui se connecte aux données FoxPro que vous souhaitez interroger et cliquer sur OK.  
  
5.  Dans la boîte de dialogue Import Objects, sélectionnez une ou plusieurs tables que vous souhaitez importer et cliquez sur OK. Les noms des tables Visual FoxPro que vous avez importées sont affichés dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez maintenant utiliser Microsoft Access pour manipuler les données dans les tables Visual FoxPro importées. Les données que vous importez sont un instantané des données stockées dans Visual FoxPro; les modifications que vous effectuez aux données importées ne sont pas renvoyées à la source de données Visual FoxPro.  
  
 Si vous souhaitez des modifications que vous effectuez dans Microsoft Access pour modifier les données sur la source de données Visual FoxPro, voir [requête et mise à jour des données Visuelles FoxPro de Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
