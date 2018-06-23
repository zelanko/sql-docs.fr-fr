---
title: Liens de sécurité de l’intégration CLR | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: edd8600e3c8e577ef020d732cce3924252393ce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153997"
---
# <a name="links-in-clr-integration-security"></a>Liens dans la sécurité d'intégration du CLR
  Cette section décrit la façon dont les parties de code utilisateur peuvent s'appeler dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en langage [!INCLUDE[tsql](../../includes/tsql-md.md)] ou dans l'un des langages managés. Ces relations entre objets sont connues sous le nom de liens.  
  
## <a name="invocation-links"></a>Liens d'appel  
 Les liens d'appel correspondent à un appel de code, soit un utilisateur qui appelle un objet (tel qu'un lot [!INCLUDE[tsql](../../includes/tsql-md.md)] qui appelle une procédure stockée), soit une procédure stockée ou une fonction CLR. Les liens d'appel provoquent la vérification d'une autorisation `EXECUTE` sur l'appelé.  
  
## <a name="table-access-links"></a>Liens d'accès de table  
 Les liens d'accès de table correspondent à l'extraction ou à la modification de valeurs dans une table, une vue ou une fonction table. Ils sont semblables aux liens d'appel, mais offrent un contrôle d'accès affiné en ce qui concerne les autorisations SELECT, INSERT, UPDATE et DELETE.  
  
## <a name="gated-links"></a>Liens contrôlés  
 Les liens contrôlés signifient que pendant l'exécution, les autorisations ne sont pas vérifiées dans toute la relation d'objet une fois qu'elle a été établie. Lorsqu'il y a un lien contrôlé entre deux objets (par exemple, l'objet **x** et l'objet **y**), les autorisations sur l'objet **y** et autres objets accédés à partir de l'objet **y** sont vérifiés uniquement au moment de la création de l'objet **x**. Au moment de la création de l’objet **x**, `REFERENCE` autorisation est vérifiée sur **y** par rapport au propriétaire de **x**. Lors de l'exécution (par exemple, lorsque quelqu'un appelle l'objet **x**), il n'y a aucune autorisation vérifiée par rapport à **y** ou autres objets auquel il fait  référence de manière statique. Lors de l'exécution, une autorisation appropriée est vérifiée par rapport à l'objet **x** lui-même.  
  
 Les liens contrôlés sont toujours utilisés conjointement à une dépendance de métadonnées entre deux objets. Cette dépendance de métadonnées est une relation établie dans les catalogues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui empêche un objet d'être supprimé tant qu'un autre objet dépend de lui.  
  
 Les liens contrôlés sont utiles lorsqu'il n'est ni approprié ou réalisable d'accorder des autorisations à de nombreux objets dépendants. Des liens contrôlés sont introduits entre les objets qui définissent des points d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)] dans des assemblys CLR (par exemple, des procédures, déclencheurs, fonctions, types et agrégats CLR) et les assemblys à partir desquels ils sont définis. La sécurité contrôlée contre ces objets implique que pour appeler un point d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)] défini dans un assembly CLR, l'appelant n'a besoin que d'une autorisation appropriée sur ce point d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'appelant n'est pas obligé d'avoir des autorisations sur cet assembly ou tout autre assembly auquel il fait référence de manière statique. Les autorisations sur l'assembly sont vérifiées au moment de la création du point d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="sql-server-authorization-based-security"></a>Sécurité SQL Server basée sur l'autorisation  
 Vous trouverez ci-dessous les règles de base sous-jacentes aux contrôles de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les appels de et entre des objets de base de données basés sur le CLR ; les trois premières règles définissent les autorisations qui sont contrôlées et contre quel objet ; la quatrième règle définit le contexte d'exécution par rapport auquel l'autorisation est contrôlée.  
  
1.  Tous les appels requièrent l'autorisation `EXECUTE`, à moins que les appels ne se produisent dans le même objet ; cela signifie que les appels dans le même assembly ne nécessitent aucun contrôle d'autorisation. L'autorisation est contrôlée au moment de l'exécution.  
  
2.  Les liens contrôlés requièrent l'autorisation `REFERENCE` par rapport à l'appelé lorsque l'objet appelant est créé. L'autorisation est contrôlée pour le propriétaire de l'objet appelant lorsque l'objet est créé.  
  
3.  Les liens d'accès de table requièrent l'autorisation `SELECT`, `INSERT`, `UPDATE` ou `DELETE` correspondant pra rapport à la table ou vue qui est accédée.  
  
4.  L'autorisation est contrôlée par rapport au contexte d'exécution actuel. Il est possible de créer des procédures et fonctions avec un contexte d'exécution différent de l'appelant. Un assembly est toujours créé avec le contexte d'exécution de la procédure, de la fonction ou du déclencheur défini contre lui.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  