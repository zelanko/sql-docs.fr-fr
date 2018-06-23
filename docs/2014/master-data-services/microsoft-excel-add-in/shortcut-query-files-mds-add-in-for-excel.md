---
title: Fichiers de requête de raccourci (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ba19131fdb06d5e8e71071663a6fc0a81c3d51cf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041142"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>Fichiers de requête de raccourci (Complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], utilisez les fichiers de requête de raccourci pour rapidement vous connecter et charger les données fréquemment utilisées. Vous pouvez également utiliser ces fichiers lorsque vous souhaitez partager des données MDS avec d'autres utilisateurs. Au lieu d'enregistrer la feuille de calcul et de l'envoyer par courrier électronique, vous pouvez enregistrer un fichier de requête de raccourci et l'envoyer de la même manière. De cette façon, vous êtes sûr que votre destinataire et vous-même êtes connectés au référentiel MDS pour récupérer les données les plus récentes.  
  
 Les fichiers de requête de raccourci sont des fichiers XML qui contiennent des informations sur :  
  
-   la connexion au référentiel MDS ;  
  
-   le modèle, la version, et l'entité ;  
  
-   tous les filtres appliqués lorsque le raccourci a été créé ;  
  
-   l'ordre de gauche à droite des colonnes lorsque le raccourci a été créé.  
  
 Vous pouvez enregistrer ces fichiers dans une liste et les choisir lorsque vous ouvrez le complément. Vous pouvez les exporter sur votre ordinateur ou dans un emplacement partagé, ou vous pouvez les envoyer à d'autres utilisateurs.  
  
## <a name="queryopener-application"></a>Application QueryOpener  
 Tous les utilisateurs qui installent [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] installent également une application appelée QueryOpener. Cette application sert à ouvrir des fichiers de requête de raccourci dans [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]. Si vous double-cliquez sur le fichier de requête de raccourci, cette application est automatiquement lancée pour ouvrir le fichier dans le complément.  
  
 Lorsque vous ouvrez un fichier de requête de raccourci avec cette application, vous êtes invité à créer une connexion « sécurisée », indiquant que vous faites confiance au contenu de cet emplacement. Chaque fois que vous marquez une connexion comme sécurisée, elle est ajouté à la liste. Si vous souhaitez effacer cette liste, ouvrez la boîte de dialogue **Paramètres** , puis dans la section **Serveurs ajoutés à la liste sécurisée** , cliquez sur **Effacer tout**.  
  
 L’emplacement par défaut pour l’application est *lecteur*: \Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
 Il existe deux manières d'ouvrir des fichiers de requête de raccourci : vous pouvez les importer ou bien double-cliquer sur leur icône pour les ouvrir automatiquement.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Enregistrez le contenu de la feuille de calcul active en tant que fichier de requête de raccourci.|[Enregistrer un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Envoyez par courrier électronique un fichier de requête de raccourci qui représente le contenu de la feuille de calcul active.|[Envoyer par e-mail un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Connexions &#40;Complément MDS pour Excel#41;](connections-mds-add-in-for-excel.md)  
  
-   [Complément Master Data Services pour Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  