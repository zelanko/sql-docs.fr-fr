---
title: "Se connecter au serveur (page Paramètres de connexion supplémentaires) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7befc61bcf4a973aa0593e476bcce76f5751f40b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-additional-connection-parameters-page"></a>Se connecter au serveur (page Paramètres de connexion supplémentaires)
La boîte de dialogue **Se connecter à** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] présente les valeurs de chaîne de connexion les plus courantes sous forme d’options. Vous pouvez utiliser la page **Paramètres de connexion supplémentaires** pour ajouter d’autres paramètres de connexion à la chaîne de connexion.  
  
-   Les paramètres de connexion supplémentaires peuvent être n'importe quels paramètres de connexion ODBC.  
  
-   Les paramètres de connexion supplémentaires doivent être ajoutés sous la forme **;paramètre1=valeur1;paramètres2=valeur2**.  
  
-   Les paramètres ajoutés à partir de la page **Paramètres de connexion supplémentaires** sont ajoutés aux paramètres sélectionnés par le biais des options de la boîte de dialogue **Se connecter à** .  
  
-   La dernière instance de chaque paramètre fourni remplace toutes les instances précédentes du paramètre. Les paramètres ajoutés par le biais de la page **Paramètres de connexion supplémentaires** suivent et remplacent les paramètres fournis sous l’onglet **Connexion** ou **Propriétés de connexion** . Par exemple, si l’onglet **Connexion** fournit **SERVEUR1** comme **Nom du serveur**et si la page **Paramètres de connexion supplémentaires** indique **SERVEUR=SERVEUR2**, la connexion sera établie à **SERVEUR2**.  
  
-   Les paramètres ajoutés à l’aide de la page **Paramètres de connexion supplémentaires** sont toujours transmis sous forme de texte brut.  
  
    > [!IMPORTANT]  
    > Évitez d’ajouter des informations d’identification de connexion et des mots de passe dans la page **Paramètres de connexion supplémentaires** . Ceux-ci ne seront pas chiffrés lorsqu'ils seront transmis sur le réseau. Utilisez pour cela l’onglet **Connexion** .  
  
## <a name="task-list"></a>Liste des tâches  
  
### <a name="to-show-the-additional-connection-parameters-page"></a>Pour afficher la page Paramètres de connexion supplémentaires  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)], dans le menu **Requête** , pointez sur **Connexion**, puis cliquez sur **Se connecter**.  
  
2.  Dans la boîte de dialogue **Se connecter à** , cliquez sur **Options**, puis sur l’onglet **Paramètres de connexion supplémentaires** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-a-connecting-to-the-database-engine"></a>Exemple A : connexion au moteur de base de données  
Pour vous connecter à la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] sur un serveur nommé ACCOUNTING, entrez la ligne suivante dans la page **Paramètres de connexion supplémentaires** :  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a>Exemple B : connexion à Analysis Services  
Pour vous connecter à des serveurs d’analyse, définir un délai d’expiration de l’écriture différée de 5 et faire en sorte que toutes les partitions à l’écoute des notifications soient interrogées en temps réel (en évitant la mise en cache), entrez la ligne suivante dans la page **Paramètres connexion supplémentaires** :  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  

