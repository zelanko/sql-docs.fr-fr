---
title: Broker:Forwarded Message Sent, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Forwarded Message Sent event class
ms.assetid: d0ef74d9-a4ef-4918-aa21-6b267e85569f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 51784663fdfec66f851bed479184ae21170a3681
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62664005"
---
# <a name="brokerforwarded-message-sent-event-class"></a>Broker:Forwarded Message Sent, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement Broker:Forwarded Message Sent quand Service Broker transmet un message.  
  
## <a name="brokerforwarded-message-sent-event-class-data-columns"></a>Colonnes de données de la classe d'événements Broker:Forwarded Message Sent  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|BigintData1|`bigint`|Numéro de séquence du message.|52|Non|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DBUserName|`nvarchar`|ID d'instance de broker pour le service dont provient le message.|40|Non|  
|EventClass|`int`|Type de classe d'événements capturée. Toujours 139 pour Broker:Forwarded Message Sent.|27|Non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|Non|  
|FileName|`nvarchar`|Nom du service auquel le message est destiné.|36|Non|  
|GUID|`uniqueidentifier`|ID de conversation du dialogue. Cet identifiant est transmis en tant que partie intégrante du message et est partagé par les deux intervenants de la conversation.|54|Non|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IndexID|`int`|Nombre de sauts restants au message transféré.|24|Non|  
|IntegerData|`int`|Nombre de fragments du message transféré.|25|Non|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Non|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|ObjectId|`int`|Valeur de durée de vie du message transmis au moment de sa transmission.|22|Non|  
|ObjectName|`nvarchar`|ID du message transféré.|34|Non|  
|OwnerName|`nvarchar`|Identificateur de Service Broker vers lequel le message est dirigé.|37|Non|  
|RoleName|`nvarchar`|Rôle du descripteur de conversation. Valeurs possibles :<br /><br /> Initiateur. Cette instance de Service Broker a lancé la conversation.<br /><br /> Cible. Cette instance de Service Broker correspond à la cible de la conversation.|38|Non|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|SPID|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|StartTime|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|Opération réussie|`int`|Temps consommé durant le processus de transfert.|23|Non|  
|TargetLoginName|`nvarchar`|Adresse réseau à laquelle cette instance a envoyé le message. Notez que celle-ci peut différer de la destination finale du message.|42|Non|  
|TargetUserName|`nvarchar`|Nom du service initiateur du message.|39|Non|  
|TransactionID|`bigint`|ID affecté à la transaction par le système.|4|Non|  
  
  
