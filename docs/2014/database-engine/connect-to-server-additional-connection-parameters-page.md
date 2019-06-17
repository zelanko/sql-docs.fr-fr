---
title: Se connecter au serveur (page Paramètres de connexion supplémentaires) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e92fbb8bc29aed54e43925a0670d9a365388df62
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62808670"
---
# <a name="connect-to-server-additional-connection-parameters-page"></a>Se connecter au serveur (page Paramètres de connexion supplémentaires)
  La boîte de dialogue **Se connecter à** de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] présente les valeurs de chaîne de connexion les plus courantes sous forme d’options. Vous pouvez utiliser la page **Paramètres de connexion supplémentaires** pour ajouter d’autres paramètres de connexion à la chaîne de connexion.  
  
-   Les paramètres de connexion supplémentaires peuvent être n'importe quels paramètres de connexion ODBC.  
  
-   Les paramètres de connexion supplémentaires doivent être ajoutés sous la forme **;paramètre1=valeur1;paramètres2=valeur2**.  
  
-   Les paramètres ajoutés à partir de la page **Paramètres de connexion supplémentaires** sont ajoutés aux paramètres sélectionnés par le biais des options de la boîte de dialogue **Se connecter à** .  
  
-   La dernière instance de chaque paramètre fourni remplace toutes les instances précédentes du paramètre. Les paramètres ajoutés par le biais de la page **Paramètres de connexion supplémentaires** suivent et remplacent les paramètres fournis sous l’onglet **Connexion** ou **Propriétés de connexion** . Par exemple, si l’onglet **Connexion** fournit **SERVEUR1** comme **Nom du serveur**et si la page **Paramètres de connexion supplémentaires** indique **SERVEUR=SERVEUR2**, la connexion sera établie à **SERVEUR2**.  
  
-   Les paramètres ajoutés à l’aide de la page **Paramètres de connexion supplémentaires** sont toujours transmis sous forme de texte brut.  
  
    > [!IMPORTANT]  
    >  Évitez d’ajouter des informations d’identification de connexion et des mots de passe dans la page **Paramètres de connexion supplémentaires** . Ceux-ci ne seront pas chiffrés lorsqu'ils seront transmis sur le réseau. Utilisez pour cela l’onglet **Connexion** .  
  
## <a name="task-list"></a>Liste des tâches  
  
### <a name="to-show-the-additional-connection-parameters-page"></a>Pour afficher la page Paramètres de connexion supplémentaires  
  
1.  Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], dans le menu **Requête** , pointez sur **Connexion**, puis cliquez sur **Se connecter**.  
  
2.  Dans la boîte de dialogue **Se connecter à** , cliquez sur **Options**, puis sur l’onglet **Paramètres de connexion supplémentaires** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-a-connecting-to-the-database-engine"></a>Exemple a : Connexion au moteur de base de données  
 Pour vous connecter à la base de données [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] sur un serveur nommé ACCOUNTING, entrez la ligne suivante dans la page **Paramètres de connexion supplémentaires** :  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a>Exemple b : Connexion à Analysis Services  
 Pour vous connecter à des serveurs d’analyse, définir un délai d’expiration de l’écriture différée de 5 et faire en sorte que toutes les partitions à l’écoute des notifications soient interrogées en temps réel (en évitant la mise en cache), entrez la ligne suivante dans la page **Paramètres connexion supplémentaires** :  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  
  
