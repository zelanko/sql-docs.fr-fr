---
title: Accès aux données depuis les objets de base de données CLR | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab43297c592258075e9c80ec9808b10c7bd267df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051553"
---
# <a name="data-access-from-clr-database-objects"></a>Accès aux données à partir d'objets de base de données CLR
  Une routine du common language runtime (CLR) peut accéder facilement aux données stockées dans l’instance de [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] dans lequel elle s’exécute, ainsi que les données stockées dans les instances distantes. Les données particulières auxquelles la routine peut accéder sont déterminées par le contexte utilisateur dans lequel le code s'exécute. Accéder aux données à partir d’un objet de base de données CLR à l’aide du fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les données à partir de clients gérés et les applications de couche intermédiaire. C'est la raison pour laquelle vous pouvez tirer parti de vos connaissances d'ADO.NET et de `SqlClient` dans les applications clientes managées et de couche intermédiaire.  
  
> [!NOTE]  
>  Les méthodes de type défini par l'utilisateur et les fonctions définies par l'utilisateur ne sont pas autorisées à effectuer un accès aux données par défaut. Vous devez définir la propriété `DataAccess` de `SqlMethodAttribute` ou `SqlFunctionAttribute` à `DataAccessKind.Read` pour permettre l'accès aux données en lecture seule à partir des méthodes de type défini par l'utilisateur ou des fonctions définies par l'utilisateur. Les opérations de modification des données ne sont pas autorisées à partir des types définis par l'utilisateur ou des fonctions définies par l'utilisateur ; par ailleurs, elles lèvent des exceptions au moment de l'exécution, à la moindre tentative.  
  
 Cette section décrit uniquement les différences spécifiques en matière de fonctionnement et de comportement lors de l'accès aux données à partir d'un objet de base de données CLR. Pour plus d'informations sur les fonctionnalités d'ADO.NET, consultez la documentation ADO.NET incluse dans le Kit de développement logiciel .NET Framework (SDK).  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Connexion contextuelle](context-connection.md)  
 Décrit la connexion contextuelle à SQL Server.  
  
 [Emprunt d’identité et informations d’identification pour les connexions](impersonation-and-credentials-for-connections.md)  
 Décrit l'emprunt d'identité et les informations d'identification des connexions.  
  
 [Extensions spécifiques in-process de SQL Server à ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Décrit les objets in-process `SqlPipe`, `SqlContext`, `SqlTriggerContext` et `SqlDataRecord` spécifiques.  
  
 [Intégration et transactions du CLR](../../native-client-ole-db-transactions/transactions.md)  
 Explique comment la nouvelle infrastructure de transaction fournie dans l'espace de noms System.Transactions s'intègre à ADO.NET et décrit l'intégration du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Sérialisation XML à partir des objets de base de données CLR](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 Explique comment activer les scénarios de sérialisation XML des objets de base de données CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  