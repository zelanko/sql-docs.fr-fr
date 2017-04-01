---
title: "Autorisations Invit&#233; sur les bases de donn&#233;es utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "meilleures pratiques [moteur de base de données]"
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Autorisations Invit&#233; sur les bases de donn&#233;es utilisateur
  Cette règle détermine si l'utilisateur invité a l'autorisation d'accéder à la base de données. Cette règle s'applique uniquement aux bases de données utilisateur.  
  
## Meilleures pratiques recommandées  
 Révoquez l'autorisation d'accès à la base de données octroyée à l'utilisateur invité si elle n'est pas nécessaire.  
  
 Vous ne pouvez pas supprimer l’utilisateur guest, mais vous pouvez le désactiver en révoquant son autorisation CONNECT. Pour ce faire, vous devez exécuter REVOKE CONNECT FROM GUEST dans toute base de données autre que la base master, tempdb ou msdb.  
  
## Pour plus d'informations  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  