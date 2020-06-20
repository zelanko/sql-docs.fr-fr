---
title: 'Tâche 4 : exportation des résultats de l’activité de correspondance dans un fichier Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd85a523804232deff14f2e1da5485229f943dd2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84999659"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>Tâche 4 : Exportation des résultats de l’activité de mise en correspondance dans un fichier Excel
  Dans cette tâche, vous allez exporter les résultats de l'activité de mise en correspondance dans un fichier Excel.

1.  Dans la page **Exporter** , sélectionnez **fichier Excel** pour le **type de destination**.

2.  Sélectionnez l’option **résultats de survie** . Dans le processus de survie, DQS détermine un enregistrement survivant pour chaque cluster en fonction de la **règle de survie** que vous avez sélectionnée.

3.  Cliquez sur **Parcourir** et accédez au dossier dans lequel vous souhaitez stocker le fichier de sortie.

4.  Tapez **nettoyer et faire correspondre Suppliers.xls** pour le nom et cliquez sur **ouvrir**.

5.  Vérifiez que l' **enregistrement pivot** est sélectionné pour la **règle de survie**. Lorsque vous sélectionnez cette option, l'enregistrement pivot de chaque cluster est choisi pour la sortie d'un cluster. Les autres options de la règle de survivance sont les suivantes :

    1.  **Enregistrement le plus complet :** L’enregistrement survivant est celui avec le plus grand nombre de champs remplis.

    2.  **Enregistrement le plus long :** L’enregistrement survivant est celui avec le plus grand nombre de termes dans les champs sources.

    3.  **Enregistrement le plus complet et le plus long :** L’enregistrement survivant est celui avec le plus grand nombre de champs remplis et contient le plus grand nombre de termes dans chaque champ.

     ![Exporter les résultats à partir de la Page de correspondance](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Exporter les résultats à partir de la Page de correspondance")

6.  Cliquez sur **Exporter** pour exporter les résultats vers un fichier Excel.

7.  Cliquez sur **Fermer** pour fermer la boîte de dialogue **Exporter correspondante** .

8.  Cliquez sur **Terminer** pour terminer l’activité de correspondance.

9. Ouvrez le fichier **nettoyé et mis en correspondance Suppliers.xlsx** et vérifiez que vous ne voyez pas de doublons (RéfFournisseur).

 À présent, les données des fournisseurs ont été nettoyées et mises en correspondance pour supprimer les doublons.

## <a name="next-step"></a>étape suivante
 [Leçon 4 : Stockage des données sur les fournisseurs dans MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


