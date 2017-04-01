---
title: "Se connecter au serveur (Oracle), Connexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.login.f1"
helpviewer_keywords: 
  - "boîte de dialogue Se connecter au serveur, réplication"
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Se connecter au serveur (Oracle), Connexion
  Utilisez la **connexion** onglet de le **se connecter au serveur** boîte de dialogue pour spécifier le compte sous lequel les connexions sont établies à partir de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de distribution pour le serveur de publication Oracle. Vous devez utiliser le compte défini pour le schéma utilisateur d'administration de réplication au cours de la configuration du serveur de publication. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Options  
 **Instance de serveur**  
 Nom TNS (Transparent Network Substrate) du serveur de publication Oracle, défini au cours de la configuration du logiciel client Oracle installé sur le serveur de distribution.  
  
 **Authentification**  
 Sélectionnez **l’authentification Standard Oracle** (recommandé) ou **l’authentification Windows**. Si vous sélectionnez **l’authentification Windows**:  
  
-   Le serveur Oracle doit être configuré pour permettre les connexions en utilisant les informations d'identification Windows. Pour plus d'informations, consultez votre documentation Oracle.  
  
-   Vous devez être connecté avec le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que vous avez défini pour le schéma utilisateur d'administration de réplication.  
  
 **Connexion** et **mot de passe**  
 Si vous avez sélectionné **l’authentification Standard Oracle** pour le **l’authentification** option, spécifiez la connexion et le mot de passe à utiliser, qui doit être identique à celui spécifié pour le schéma utilisateur administratif de réplication.  
  
## Voir aussi  
 [Glossaire des termes de la publication Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  