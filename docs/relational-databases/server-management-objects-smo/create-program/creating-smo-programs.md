---
title: "Création de programmes SMO | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cd8d9fa33596bd200816c7d2e65213646c9e8344
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="creating-smo-programs"></a>Création de programmes SMO
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Programmation générale de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) inclut les zones communes que tous les objets partagent, telles que les méthodes, propriétés de paramètre en cours d’exécution et la manipulation de collections des objets.  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Connexion à une instance de SQL Server](../../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)|Programme SMO le plus élémentaire établissant une connexion avec une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Démontre l'authentification Windows et l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Inclut aussi des exemples qui illustrent la connexion à une instance locale et distante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Déconnexion d’une instance de SQL Server](../../../relational-databases/server-management-objects-smo/create-program/disconnecting-from-an-instance-of-sql-server.md)|Programme montrant comment se déconnecter de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Appel de méthodes](../../../relational-databases/server-management-objects-smo/create-program/calling-methods.md)|Cette section décrit l'approche générale des méthodes d'appel. Illustre l'utilisation des paramètres et la façon de gérer les tables de données retournées dans un objet <xref:System.Data.DataTable>. Inclut aussi un exemple de comment appeler un constructeur d’objet et comment appeler le **Clone** (méthode).|  
|[Définition de propriétés - SMO](../../../relational-databases/server-management-objects-smo/create-program/setting-properties-smo.md)|Cette section décrit comment définir différents types de propriétés. Explique comment définir et obtenir les propriétés d'objet. Inclut aussi des exemples qui définissent les propriétés d'objet lors de la création de l'objet et montre comment itérer à travers toutes les propriétés d'un objet.|  
|[Utilisation de collections](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md)|Différents programmes qui traitent des techniques utilisées avec les collections d'objets. Indique comment faire référence à un objet à l'aide de collections. Inclut aussi un exemple de la façon d'itérer à travers les membres d'une collection.|  
|[Gestion des événements SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-events.md)|Cette section décrit comment installer et gérer les événements dans SMO. Inclut un exemple sur la façon d'installer un gestionnaire d'événements et un abonnement aux événements.|  
|[Gestion des exceptions SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md)|Cette section décrit comment intercepter les exceptions dans SMO. Inclut des exemples sur la façon d'intercepter une exception et sur la façon d'afficher une exception interne.|  
|[Utilisation des types de données](../../../relational-databases/server-management-objects-smo/create-program/working-with-data-types.md)|Cette section décrit comment utiliser les différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Décrit comment construire un type de données avec les spécifications du constructeur d'objet. Inclut aussi un exemple sur la façon de créer un type de données en utilisant le constructeur par défaut.|  
|[Utilisation de transactions](../../../relational-databases/server-management-objects-smo/create-program/using-transactions.md)|Cette section décrit comment implémenter le traitement transactionnel dans un programme SMO. Inclut un exemple sur la façon d'utiliser les transactions dans un programme SMO.|  
|[Utilisation du mode de capture](../../../relational-databases/server-management-objects-smo/create-program/using-capture-mode.md)|Cette section décrit comment enregistrer la sortie du programme SMO. L'exemple enregistre le programme SMO comme instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] adressées à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en vue d'une exécution ultérieure.|  
  
  
