---
title: 'Tâche 4 : Exportez les résultats à partir de l’activité vers un fichier Excel de correspondance | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c9424f2ba21fb4b93e359c8662974a82c62b4895
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020440"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>Tâche 4 : Exportation des résultats de l'activité de mise en correspondance dans un fichier Excel
  Dans cette tâche, vous allez exporter les résultats de l'activité de mise en correspondance dans un fichier Excel.  
  
1.  Dans le **exporter** page, sélectionnez **fichier Excel** pour le **Type de Destination**.  
  
2.  Sélectionnez **les résultats de SURVIVANCE** option. Dans le processus de SURVIVANCE, DQS détermine un enregistrement survivant pour chaque cluster basé sur le **règle de SURVIVANCE** que vous avez sélectionné.  
  
3.  Cliquez sur **Parcourir** et accédez au dossier où vous souhaitez stocker le fichier de sortie.  
  
4.  Type **Cleansed and Matched Suppliers.xls** pour le nom et cliquez sur **Open**.  
  
5.  Vérifiez que **enregistrement Pivot** est sélectionné pour le **règle de SURVIVANCE**. Lorsque vous sélectionnez cette option, l'enregistrement pivot de chaque cluster est choisi pour la sortie d'un cluster. Les autres options de la règle de survivance sont les suivantes :  
  
    1.  **Enregistrement le plus complet :** l'enregistrement survivant est celui contenant le plus grand nombre de champs remplis.  
  
    2.  **Enregistrement le plus long :** l'enregistrement survivant est celui contenant le plus grand nombre de termes dans les champs sources.  
  
    3.  **Enregistrement plus complet et le plus long :** l'enregistrement survivant est celui avec le plus grand nombre de champs remplis, et le plus grand nombre de termes dans chaque champ.  
  
     ![Exporter les résultats de la Page de correspondance](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "exporter les résultats de la Page de correspondance")  
  
6.  Cliquez sur **exporter** pour exporter les résultats vers un fichier Excel.  
  
7.  Cliquez sur **fermer** pour fermer la **exportation de correspondance** boîte de dialogue.  
  
8.  Cliquez sur **Terminer** pour terminer l’activité de correspondance.  
  
9. Ouvrez le **Cleansed and Matched Suppliers.xlsx** de fichiers et de confirmer que vous ne voyez pas tous les doublons (SupplierID).  
  
 À présent, les données des fournisseurs ont été nettoyées et mises en correspondance pour supprimer les doublons.  
  
## <a name="next-step"></a>Étape suivante  
 [Leçon 4 : Stockage des données des fournisseurs dans MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
