---
title: Importation de données dans Microsoft Excel à partir d’une base de données FoxPro visuelle (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bfd86233e5a0a406febcb30bf7a4fae595e53d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287669"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro
Vous pouvez importer des données Visual FoxPro dans votre feuille de travail Microsoft Excel si vous avez défini une source de données pour cela. Pour plus d’informations sur la création d’une source de données Visual FoxPro, voir [Accéder à une source de données FoxPro visuelle de Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Pour importer des données Visual FoxPro dans une feuille de travail Microsoft Excel  
  
1.  Ouvrez une feuille de calcul Microsoft Excel.  
  
2.  Dans le menu Data, choisissez Get External Data. Microsoft Query ouvre.  
  
3.  Dans la boîte de dialogue Select Data Source, sélectionnez une source de données Visual FoxPro, puis cliquez sur Use.  
  
4.  Si la base de données consultée par votre source de données comprend des tables, sélectionnez une table à partir de la boîte de dialogue Add Tables. Microsoft Query affiche la table ajoutée dans la moitié supérieure du concepteur de requêtes.  
  
    > [!NOTE]  
    >  La liste des propriétaires n’est pas disponible dans cette boîte de dialogue parce que le conducteur ne prend pas en charge les propriétaires. La liste de base de données n’est pas disponible parce que le pilote ne prend pas en charge plusieurs bases de données dans une source de données.  
  
5.  Sélectionnez les champs pour votre requête en les faisant glisser de la table sur la moitié inférieure du concepteur.  
  
6.  Fermez Microsoft Query. Les données que vous avez sélectionnées sont importées dans votre feuille de calcul Microsoft Excel.
