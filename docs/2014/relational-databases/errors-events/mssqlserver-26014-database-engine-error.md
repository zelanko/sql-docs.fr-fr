---
title: MSSQLSERVER_26014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 39245a47417ea81a0454e82ac7f76b2d6cd9e6f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042243"
---
# <a name="mssqlserver26014"></a>MSSQLSERVER_26014
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|26014|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SNI_SSL_USER_CERT_FAILURE|  
|Texte du message|Impossible de charger un certificat spécifié par l'utilisateur [Cert Hash(sha1) "%hs"]. Le serveur n'acceptera pas de connexion. Vérifiez que ce certificat est installé correctement. Consultez "Configuration du certificat en vue de son utilisation par SSL" dans la documentation en ligne.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a essayé de charger le certificat nommé dans le message, mais l’opération a échoué. Ce problème doit être résolu pour que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puisse utiliser ce certificat.  
  
 Cette erreur peut avoir plusieurs causes :  
  
-   Le certificat peut avoir été déplacé ou supprimé.  
  
-   Si la connexion utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a changé, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut ne pas avoir l'autorisation d'accéder au certificat.  
  
-   Le certificat a peut-être expiré.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Assurez-vous que le certificat nommé dans le message existe sur le système, qu'il est accessible et qu'il est toujours valide.  
  
  