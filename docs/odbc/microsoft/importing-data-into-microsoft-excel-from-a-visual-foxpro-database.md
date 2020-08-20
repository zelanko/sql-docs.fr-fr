---
description: Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro
title: Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro | Microsoft Docs
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
ms.openlocfilehash: 9a4bd1cf7983ed0a552de4f9d0f491960b48f0d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500292"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro
Vous pouvez importer des données Visual FoxPro dans votre feuille de calcul Microsoft Excel si vous avez défini une source de données pour celle-ci. Pour plus d’informations sur la création d’une source de données Visual FoxPro, consultez [accès à une source de données Visual FoxPro à partir de Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Pour importer des données Visual FoxPro dans une feuille de calcul Microsoft Excel  
  
1.  Ouvrez une feuille de calcul Microsoft Excel.  
  
2.  Dans le menu données, choisissez données externes. Microsoft Query s’ouvre.  
  
3.  Dans la boîte de dialogue Sélectionner une source de données, sélectionnez une source de données Visual FoxPro, puis cliquez sur utiliser.  
  
4.  Si la base de données accessible par votre source de données comprend des tables, sélectionnez une table dans la boîte de dialogue Ajouter des tables. Microsoft Query affiche la table ajoutée dans la moitié supérieure du concepteur de requêtes.  
  
    > [!NOTE]  
    >  La liste de propriétaires n’est pas disponible dans cette boîte de dialogue, car le pilote ne prend pas en charge les propriétaires. La liste des bases de données n’est pas disponible, car le pilote ne prend pas en charge plusieurs bases de données dans une source de données.  
  
5.  Sélectionnez les champs de votre requête en les faisant glisser de la table vers la moitié inférieure du concepteur.  
  
6.  Fermez Microsoft Query. Les données que vous avez sélectionnées sont importées dans votre feuille de calcul Microsoft Excel.
