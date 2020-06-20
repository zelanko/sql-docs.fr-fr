---
title: MSSQL_ENG024070 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c10b9071fb821acc284c5d52621ed582c526ed62
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057127"
---
# <a name="mssql_eng024070"></a>MSSQL_ENG024070
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|24070|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le client ne dispose pas d'un privilège qui est obligatoire.|  
  
## <a name="explanation"></a>Explication  
 C'est une erreur générale qui peut être déclenchée qu'une réplication soit utilisée ou non. Dans le cas d'un serveur appartenant à une topologie de réplication, l'erreur est généralement déclenchée car le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est modifié à l'aide du Gestionnaire de contrôle des services [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows et non du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Lorsque vous essayez d'exécuter un travail d'agent après avoir modifié le compte de service, le travail peut échouer avec un message d'erreur similaire au message suivant :  
  
 «Exécuté en tant qu’utilisateur : \<UserAccount> . Réplication-sous-système d’instantané de réplication : échec de l’agent \<AgentName> . Exécuté en tant qu’utilisateur : \<UserAccount> . Le client ne dispose pas d'un privilège qui est obligatoire. L'étape a échoué. `[SQLSTATE 42000] (Error 14151)`. L'étape a échoué. »  
  
 Ce problème est dû au fait que le Gestionnaire de contrôle des services Windows ne peut pas accorder les autorisations requises au nouveau compte de service pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour éviter ce problème à l'avenir, utilisez toujours le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la place du Gestionnaire de contrôle des services Windows pour modifier les comptes de service et les mots de passe.  
  
 Pour résoudre ce problème, à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , rétablissez le compte d'origine. Ensuite, à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , passez au nouveau compte. Lors de cette opération, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ajoute le nouveau compte au groupe de sécurité suivant :  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 En tant que membre de ce groupe de sécurité, le nouveau compte est habilité à exécuter le travail de l'agent de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des erreurs et des événements &#40;&#41;de réplication](errors-and-events-reference-replication.md)   
 [Gérer les connexions et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md)  
  
  
