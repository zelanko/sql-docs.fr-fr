---
title: Créer un environnement multiserveur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bacf87c25d7949580eb3d366467e1dae9381e8a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48115589"
---
# <a name="create-a-multiserver-environment"></a>Créer un environnement multiserveur
  L'administration multiserveur nécessite que vous configuriez un serveur maître (MSX) et au moins un serveur cible (TSX). Les travaux qui seront traités sur l'ensemble des serveurs cibles sont d'abord définis sur le serveur maître, puis téléchargés sur les serveurs cibles.  
  
 Par défaut, le chiffrement SSL (Secure Sockets Layer) complet et la validation de certificats sont activés pour les connexions entre les serveurs maîtres et les serveurs cible par défaut. Pour plus d’informations, consultez [Définir des options de chiffrement sur des serveurs cibles](set-encryption-options-on-target-servers.md).  
  
 Si vous avez un grand nombre de serveurs cibles, évitez de définir votre serveur maître sur un serveur de production qui doit assurer des performances élevées pour d'autres fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en effet, le trafic du serveur cible peut ralentir les performances du serveur de production. De plus, si vous transmettez des événements vers un serveur maître dédié, vous pouvez centraliser l'administration sur un seul serveur. Pour plus d’informations, consultez [Gérer les événements](manage-events.md).  
  
> [!NOTE]  
>  Pour utiliser le traitement de travaux multiserveurs, le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du rôle de base de données **TargetServersRole** de la base de données **msdb** sur le serveur maître. L'Assistant Serveur maître ajoute automatique le compte de service à ce rôle au cours du processus d'inscription.  
  
## <a name="considerations-for-multiserver-environments"></a>Considérations relatives aux environnements multiserveurs  
 Consultez la table ci-dessous pour les configurations de MSX/TSX prises en charge.  
  
||**TSX = 7.0**|**TSX = 8.0 &LT; SP3**|**TSX = 8.0 SP3 ou version ultérieure**|**TSX = 9.0**|**TSX = 10.0**|**TSX = 10.5**|**TSX = 11.0**|  
|-|--------------------|---------------------------|----------------------------------|--------------------|--------------------|---------------------|---------------------|  
|**MSX = 7.0**|Oui|Oui|non|non|non|non|non|  
|**MSX = 8.0 &LT; SP3**|Oui|Oui|non|non|non|non|non|  
|**MSX = 8.0 SP3 ou version ultérieure**|non|non|Oui|Oui|Oui|Oui|Oui|  
|**MSX = 9.0**|non|non|non|Oui|Oui|Oui|Oui|  
|**MSX = 10.0**|non|non|non|non|Oui|Oui|Oui|  
|**MSX = 10.5**|non|non|non|non|non|Oui|Oui|  
|**MSX = 11.0**|non|non|non|non|non|non|Oui|  
  
 Tenez compte des éléments ci-dessous avant de créer un environnement multiserveur :  
  
-   Chaque serveur cible dépend d’un seul serveur maître. Vous devez annuler l'inscription d'un serveur cible d'un serveur maître avant de pouvoir l'inscrire sur un autre.  
  
-   Lors de la modification du nom d'un serveur cible, vous devez annuler l'inscription de celui-ci avant de modifier son nom puis l'inscrire de nouveau.  
  
-   Si vous souhaitez démanteler une configuration multiserveur, vous devez annuler l'inscription de tous les serveurs cibles dans le serveur maître.  
  
-   SQL Server Integration Services ne prend en charge que les serveurs cibles qui présentent la même version ou une version ultérieure à la version du serveur maître.  
  
## <a name="related-tasks"></a>Tâches associées  
 Les rubriques suivantes décrivent les tâches généralement impliquées dans la création d'un environnement multiserveur.  
  
|Description|Rubrique|  
|-----------------|-----------|  
|Décrit comment créer un serveur maître.|[Créer un serveur maître](make-a-master-server.md)|  
|Décrit comment créer un serveur cible.|[Créer un serveur cible](make-a-target-server.md)|  
|Décrit comment inscrire un serveur cible sur un serveur maître.|[Inscrire un serveur cible dans un serveur maître](enlist-a-target-server-to-a-master-server.md)|  
|Décrit comment désinscrire un serveur cible d'un serveur maître.|[Annuler l’inscription d’un serveur cible dans un serveur maître](defect-a-target-server-from-a-master-server.md)|  
|Décrit comment annuler l'inscription de plusieurs serveurs cibles d'un serveur maître.|[Annuler l’inscription de plusieurs serveurs cibles dans un serveur maître](defect-multiple-target-servers-from-a-master-server.md)|  
|Décrit comment vérifier l'état d'un serveur cible.|[sp_help_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)<br /><br /> [sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)|  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys](troubleshoot-multiserver-jobs-that-use-proxies.md)  
  
  
