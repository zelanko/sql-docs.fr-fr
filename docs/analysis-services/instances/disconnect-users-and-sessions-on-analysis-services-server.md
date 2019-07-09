---
title: Déconnecter des utilisateurs et Sessions sur Analysis Services Server | Microsoft Docs
ms.date: 07/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 696c6548dadda2412566acf7fae1e2cff2b28095
ms.sourcegitcommit: 9af07bd57b76a34d3447e9e15f8bd3b17709140a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624397"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Déconnecter des utilisateurs et sessions sur un serveur Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  En tant qu’administrateur, vous souhaiterez l’activité utilisateur final dans le cadre de la gestion de la charge de travail. Pour cela, vous devez annuler les sessions et les connexions. Les sessions peuvent être formées automatiquement lorsqu'une requête est exécutée (implicite) ou nommées au moment de la création par l'administrateur (explicite). Les connexions sont des conduits ouverts par lesquels les requêtes peuvent être exécutées. Les sessions et les connexions peuvent être terminées pendant qu'elles sont actives. Par exemple, vous souhaiterez terminer le traitement d’une session si le traitement est trop long ou si vous obligent à certains doutes concernant si la commande en cours d’exécution a été écrit correctement.  
  
## <a name="ending-sessions-and-connections"></a>Arrêt des sessions et des connexions  
 Pour gérer les sessions et les connexions, utilisez les vues de gestion dynamique (DMV) et XMLA :  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance d'Analysis Services.  
  
2.  Collez l'une des requêtes DMV suivantes dans une fenêtre de requête MDX pour obtenir la liste de toutes les sessions, connexions et commandes qui s'exécutent actuellement :  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  (Cette requête ne s’applique pas à Azure Analysis Services)
  
     `Select * from $System.Discover_Commands`  
  
3.  Appuyez sur F5 pour exécuter la requête.  
  
     La requête DMV renvoie des informations relatives à la session et à la connexion sous la forme d'un tableau, facilitant ainsi la lecture et la copie des données qu'il contient.  
  
 Gardez la fenêtre de requête ouverte. Dans la prochaine étape, vous retournerez à cette page pour copier les SPID de la session de laquelle vous voulez vous déconnecter.  
  
 Pour terminer une session, ouvrez une deuxième fenêtre de requête XMLA.  
  
1.  Collez la syntaxe suivante dans une fenêtre de requête MDX, en remplaçant l'espace réservé ConnectionID, SessionID ou SPID par une valeur valide copiée dans l'étape précédente.  
  
    ```  
    <Cancel xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Appuyez sur F5 pour exécuter la commande d'annulation.  

Annulation d’un SPID/SessionID annulera toutes les commandes actives en cours d’exécution sur la session correspondant à l’élément SPID/SessionID. Annulation d’une connexion identifie la session associée à la connexion et annuler des commandes actives en cours d’exécution sur cette session. Dans de rares cas, une connexion n’est pas fermée si le moteur ne peut pas suivre toutes les sessions et SPID associés à la connexion ; par exemple, lorsque plusieurs sessions sont ouverts dans un scénario HTTP.   
  
Pour en savoir plus sur le code XMLA mentionné dans cette rubrique, consultez [méthode Execute &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) et [élément Cancel &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des connexions et des sessions &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Élément BeginSession &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [Élément EndSession &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Élément Session &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
