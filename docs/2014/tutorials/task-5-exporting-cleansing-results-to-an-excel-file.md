---
title: 'Tâche 5 : exportation des résultats du nettoyage dans un fichier Excel | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 44c926d2429a0d9842e9e9202568f73f72c89d9a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064746"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel
  Dans cette tâche, vous allez exporter les résultats de l'activité de nettoyage dans un fichier Excel. Pour plus d’informations, consultez la rubrique relative à la [phase d’exportation](https://msdn.microsoft.com/library/hh213061.aspx#Export) .  
  
1.  Dans le volet droit, sélectionnez **Excel** comme **type de destination**.  
  
2.  Cliquez sur **Parcourir**, spécifiez le nom du fichier de sortie en tant que **fournisseur nettoyé List.xls**, puis cliquez sur **ouvrir**.  
  
3.  Sélectionnez **données uniquement** pour le format de **sortie** afin d’exporter uniquement les données nettoyées. La deuxième option, **données et informations de nettoyage**, vous permet d’exporter les détails de l’activité de nettoyage, ainsi que les données nettoyées. L’option de **format standard** vous permet d’appliquer les formats de sortie que vous définissez sur un domaine aux valeurs de ce domaine. Vous n'avez pas défini de format de sortie pour un domaine dans le didacticiel.  
  
     ![Page Exporter les résultats de nettoyage](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Page Exporter les résultats de nettoyage")  
  
4.  Cliquez sur **Exporter** pour exporter les données. Ne cliquez pas encore sur **Terminer** .  
  
5.  Cliquez sur **Fermer** dans la boîte de dialogue **exportation** .  
  
6.  Cliquez sur **Terminer** pour terminer l’activité. Si vous avez oublié d’exporter les résultats avant de cliquer sur **Terminer**, cliquez sur **ouvrir le projet de qualité des données** dans la page principale du **client DQS**, sélectionnez **nettoyer la liste des fournisseurs** dans la liste des projets, puis cliquez sur **suivant** en bas de l’écran pour revenir à l’étape d' **exportation** du processus de nettoyage. Vous pouvez également basculer vers l’onglet **gérer et afficher les résultats** en cliquant sur le bouton **précédent** .  
  
7.  Ouvrez le **List.xlsdu fournisseur nettoyé** et procédez comme suit :  
  
    1.  Assurez-vous qu’il n’y a pas d’adresse de messagerie se terminant par adventure-work.com (sans le caractère') en recherchant adventure-work.com dans la feuille de calcul.  
  
    2.  Vérifiez qu’il n’y a pas de valeur **USA** dans la colonne **Country** .  
  
    3.  Recherchez **Los Angeles** et vérifiez que l' **État** est défini sur **ca**.  
  
    4.  Confirmez qu’il n’y a pas de termes **Co.**, **Corp.** et **Inc.**  
  
    5.  Supprimez la colonne **validation d’adresse** de la feuille de calcul et enregistrez le fichier Excel. Cette colonne supplémentaire correspond au domaine composite Validation d'adresses.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 6 : Importation de valeurs depuis le projet de nettoyage de la liste des fournisseurs](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
