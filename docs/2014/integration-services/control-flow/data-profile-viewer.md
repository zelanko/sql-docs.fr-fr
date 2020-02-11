---
title: Visionneuse du profil des données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], output viewer
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0f6bcad3636178fb4aebbcdbeee29ba2542f092e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832414"
---
# <a name="data-profile-viewer"></a>Visionneuse du profil des données
  L'affichage et l'analyse des profils des données sont les étapes suivantes du processus de profilage des données. Pour afficher ces profils, vous devez avoir exécuté la tâche de profilage des données dans un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et avoir calculé les profils des données. Pour plus d’informations sur la configuration et l’exécution des tâches de profilage des données, consultez [Configuration de la tâche de profilage des données](data-profiling-task.md).  
  
> [!IMPORTANT]  
>  Le fichier de sortie peut contenir des données sensibles qui concernent votre base de données et les données qu'elle contient. Pour obtenir des suggestions sur la manière de sécuriser davantage ce fichier, consultez [Accéder aux fichiers utilisés par des packages](../access-to-files-used-by-packages.md).  
  
## <a name="data-profiles"></a>Profils de données  
 Pour afficher les profils des données, vous configurez la tâche de profilage des données de manière à envoyer sa sortie à un fichier, puis vous utilisez la visionneuse du profil des données autonome. Pour ouvrir la visionneuse du profil des données, effectuez l'une des actions suivantes :  
  
-   Cliquez avec le bouton droit sur la tâche de **profilage des données** dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , puis cliquez sur **Modifier**. Cliquez sur **Ouvrir la visionneuse de profil** dans la page **Général** de **l’Éditeur de tâche de profilage de données**.  
  
-   Dans le dossier *\<lecteur>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn, exécutez DataProfileViewer.exe.  
  
 La visionneuse utilise plusieurs volets pour afficher les profils demandés et les résultats calculés avec, en option, des détails et une fonction d'exploration vers le bas :  
  
 Volet**Profils**  
 Le volet **Profils** affiche les profils demandés dans la tâche de profilage des données. Pour afficher les résultats calculés pour le profil, sélectionnez le profil dans le volet **Profils** . Les résultats apparaîtront dans les autres volets de la visionneuse.  
  
 Volet**Résultats**  
 Le volet **Résultats** résume les résultats calculés du profil sur une seule ligne. Par exemple, si vous demandez un **Profil de distribution de longueurs de colonne**, cette ligne inclut la longueur minimale et la longueur maximale, ainsi que le nombre de lignes. Pour la plupart des profils, vous pouvez sélectionner cette ligne dans le volet **Résultats** pour afficher d’autres détails dans le volet **Détails** facultatif.  
  
 Volet**Détails**  
 Pour la plupart des types de profils, le volet **Détails** affiche des informations supplémentaires à propos des résultats du profil sélectionnés dans le volet **Résultats** . Par exemple, si vous demandez un **Profil de distribution de longueurs de colonne**, le volet **Détails** affiche chaque longueur de colonne qui a été trouvée. Le volet affiche aussi le nombre et le pourcentage de lignes dans lesquelles la valeur de colonne est égale à cette longueur de colonne.  
  
 Pour les trois types de profils qui sont calculés sur plusieurs colonnes (Profil de clé candidate, Profil de dépendance fonctionnelle et Profil d’inclusion de valeur), le volet **Détails** affiche les violations de la relation attendue. Par exemple, si vous demandez un Profil de clé candidate, le volet Détails affiche les valeurs dupliquées qui enfreignent l'unicité de la clé candidate.  
  
 Si la source de données utilisée pour calculer le profil est disponible, vous pouvez double-cliquer sur une ligne dans le volet **Détails** pour consulter les lignes correspondantes de données dans le volet **Exploration vers le bas** .  
  
 Volet**Exploration vers le bas**  
 Vous pouvez double-cliquer sur une ligne dans le volet **Détails** pour consulter les lignes correspondantes de données dans le volet **Exploration vers le bas** quand les conditions suivantes sont vérifiées :  
  
-   La source de données utilisée pour calculer le profil est disponible.  
  
-   Vous êtes autorisé à afficher les données.  
  
 Pour se connecter à la base de données source lors d'une requête d'exploration vers le bas, la visionneuse du profil des données utilise l'authentification Windows et les informations d'identification de l'utilisateur actuel. La visionneuse du profil des données n'utilise pas les informations de connexion stockées dans le package qui a exécuté la tâche de profilage des données.  
  
> [!IMPORTANT]  
>  La fonction d'exploration vers le bas disponible dans la visionneuse du profil des données envoie des requêtes actives à la source de données d'origine. Ces requêtes peuvent avoir un impact négatif sur les performances du serveur.  
>   
>  Si vous descendez dans la hiérarchie à partir d'un fichier de sortie qui n'a pas été créé récemment, les requêtes d'exploration risquent de retourner un autre ensemble de lignes que celui à partir duquel la sortie d'origine a été calculée.  
  
 Pour plus d’informations sur l’interface utilisateur de la visionneuse du profil des données, consultez [Aide F1 de la visionneuse du profil des données](../data-profile-viewer-f1-help.md).  
  
  
