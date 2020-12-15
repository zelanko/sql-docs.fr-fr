---
description: Création de programmes SMO
title: Création de programmes SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 00ae0e27bb4d90c286ef1b199c200ab5b900f706
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467260"
---
# <a name="creating-smo-programs"></a>Création de programmes SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  La programmation générale d'objets SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects) inclut les zones communes que tous les objets partagent, telles que l'exécution de méthodes, la définition de propriétés et la manipulation de collections.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Connexion à une instance de SQL Server](../../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)|Programme SMO le plus élémentaire établissant une connexion avec une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Démontre l'authentification Windows et l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Inclut aussi des exemples qui illustrent la connexion à une instance locale et distante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Déconnexion d'une instance de SQL Server](../../../relational-databases/server-management-objects-smo/create-program/disconnecting-from-an-instance-of-sql-server.md)|Programme montrant comment se déconnecter de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Appel de méthodes](../../../relational-databases/server-management-objects-smo/create-program/calling-methods.md)|Cette section décrit l'approche générale des méthodes d'appel. Illustre l'utilisation des paramètres et la façon de gérer les tables de données retournées dans un objet <xref:System.Data.DataTable>. Contient également un exemple d’appel d’un constructeur d’objet et de l’appel de la méthode **clone** .|  
|[Définition de propriétés - SMO](../../../relational-databases/server-management-objects-smo/create-program/setting-properties-smo.md)|Cette section décrit comment définir différents types de propriétés. Explique comment définir et obtenir les propriétés d'objet. Inclut aussi des exemples qui définissent les propriétés d'objet lors de la création de l'objet et montre comment itérer à travers toutes les propriétés d'un objet.|  
|[Utilisation de collections](../../../relational-databases/server-management-objects-smo/create-program/using-collections.md)|Différents programmes qui traitent des techniques utilisées avec les collections d'objets. Indique comment faire référence à un objet à l'aide de collections. Inclut aussi un exemple de la façon d'itérer à travers les membres d'une collection.|  
|[Gestion des événements SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-events.md)|Cette section décrit comment installer et gérer les événements dans SMO. Inclut un exemple sur la façon d'installer un gestionnaire d'événements et un abonnement aux événements.|  
|[Gestion des exceptions SMO](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md)|Cette section décrit comment intercepter les exceptions dans SMO. Inclut des exemples sur la façon d'intercepter une exception et sur la façon d'afficher une exception interne.|  
|[Utilisation des types de données](../../../relational-databases/server-management-objects-smo/create-program/working-with-data-types.md)|Cette section décrit comment utiliser les différents types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Décrit comment construire un type de données avec les spécifications du constructeur d'objet. Inclut aussi un exemple sur la façon de créer un type de données en utilisant le constructeur par défaut.|  
|[Utilisation de transactions](../../../relational-databases/server-management-objects-smo/create-program/using-transactions.md)|Cette section décrit comment implémenter le traitement transactionnel dans un programme SMO. Inclut un exemple sur la façon d'utiliser les transactions dans un programme SMO.|  
|[Utilisation du mode de capture](../../../relational-databases/server-management-objects-smo/create-program/using-capture-mode.md)|Cette section décrit comment enregistrer la sortie du programme SMO. L'exemple enregistre le programme SMO comme instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] adressées à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en vue d'une exécution ultérieure.|  
  
  
