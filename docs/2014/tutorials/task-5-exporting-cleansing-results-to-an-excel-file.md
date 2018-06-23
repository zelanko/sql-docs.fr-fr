---
title: 'Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel | Documents Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f8a716d3b6c0007ceb89f36f23584bb4adb4f706
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039638"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel
  Dans cette tâche, vous allez exporter les résultats de l'activité de nettoyage dans un fichier Excel. Consultez [étape d’exportation](http://msdn.microsoft.com/library/hh213061.aspx#Export) pour plus d’informations.  
  
1.  Dans le volet droit, sélectionnez **Excel** pour le **le Type de Destination**.  
  
2.  Cliquez sur **Parcourir**, spécifiez le nom de fichier de sortie en tant que **Cleansed Supplier List.xls**, puis cliquez sur **ouvrir**.  
  
3.  Sélectionnez **uniquement les données** pour le **sortie** format pour exporter uniquement les données nettoyées. La deuxième option, **données et des informations sur le nettoyage**, vous permet d’exporter les détails de l’activité nettoyage avec les données nettoyées. Le **normaliser le Format** option vous permet d’appliquer les formats de sortie que vous définissez sur un domaine pour les valeurs de ce domaine. Vous n'avez pas défini de format de sortie pour un domaine dans le didacticiel.  
  
     ![Page de résultats de nettoyage de l’exportation](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Page de résultats de nettoyage de l’exportation")  
  
4.  Cliquez sur **exporter** pour exporter les données. Ne cliquez pas sur **Terminer** encore.  
  
5.  Cliquez sur **fermer** sur la **exportation** boîte de dialogue.  
  
6.  Cliquez sur **Terminer** pour terminer l’activité. Si vous avez oublié d’exporter les résultats avant de cliquer sur **Terminer**, cliquez sur **ouvrir projet de qualité des données** dans la page principale de **Client DQS**, sélectionnez **nettoyer le fournisseur Liste** dans la liste des projets, puis cliquez sur **suivant** au bas de l’écran pour accéder à la **exporter** étape du processus de nettoyage à nouveau. Vous pouvez également basculer vers **gérer et afficher les résultats** en cliquant sur **précédent** bouton.  
  
7.  Ouvrez le **Cleansed Supplier List.xls** et procédez comme suit :  
  
    1.  Vérifiez qu'aucune adresse de messagerie ne se termine par adventure-work.com (sans caractère « s ») en recherchant « adventure-work.com » dans la feuille de calcul.  
  
    2.  Voir qu’il y a aucune **USA** valeur dans le **pays** colonne.  
  
    3.  Recherchez **Los Angeles** et vérifiez que le **état** a la valeur **autorité de certification**.  
  
    4.  Confirmer qu’il n’y a pas de termes **Co.**, **corp.**, et **Inc.**.  
  
    5.  Supprimer le **Validation d’adresses** colonne à partir de la feuille de calcul et enregistrez le fichier excel. Cette colonne supplémentaire correspond au domaine composite Validation d'adresses.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 6 : Importer des valeurs à partir du projet de liste de fournisseurs de nettoyage](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  