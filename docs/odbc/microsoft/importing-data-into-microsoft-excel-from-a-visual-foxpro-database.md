---
title: "Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 615b08600c0658ba751341e1039af880d24988e4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importation de données dans Microsoft Excel à partir d’une base de données Visual FoxPro
Vous pouvez importer des données Visual FoxPro dans votre feuille de calcul Microsoft Excel si vous avez défini une source de données pour celui-ci. Pour plus d’informations sur la création d’une source de données Visual FoxPro, consultez [l’accès à une Source de données Visual FoxPro à partir de Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Pour importer des données Visual FoxPro dans une feuille de calcul Microsoft Excel  
  
1.  Ouvrez une feuille de calcul Microsoft Excel.  
  
2.  Dans le menu données, choisissez données externes. Microsoft Query s’ouvre.  
  
3.  Dans la boîte de dialogue Sélectionner une Source de données, sélectionnez une source de données Visual FoxPro et puis cliquez sur utiliser.  
  
4.  Si la base de données accédé par votre source de données comprend des tables, sélectionnez une table dans la boîte de dialogue Ajouter des Tables. Microsoft Query affiche la table ajoutée dans la moitié supérieure du Concepteur de requêtes.  
  
    > [!NOTE]  
    >  La liste des propriétaires n’est pas disponible dans cette boîte de dialogue, car le pilote ne prend pas en charge les propriétaires. La liste de la base de données n’est pas disponible, car le pilote ne prend pas en charge plusieurs bases de données dans une source de données.  
  
5.  Sélectionnez les champs de votre requête en les faisant glisser à partir de la table vers le bas la moitié du concepteur.  
  
6.  Fermez Microsoft Query. Les données que vous avez sélectionné sont importées dans votre feuille de calcul Microsoft Excel.
