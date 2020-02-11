---
title: Accès aux données à partir des objets de base de données CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4561c7b8979a919ea144bab6d9b42f722b089e48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874078"
---
# <a name="data-access-from-clr-database-objects"></a>Accès aux données à partir d'objets de base de données CLR
  Une routine de common language runtime (CLR) peut accéder facilement aux données stockées dans l' [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] instance de dans laquelle elles s’exécutent, ainsi qu’aux données stockées dans des instances distantes. Les données particulières auxquelles la routine peut accéder sont déterminées par le contexte utilisateur dans lequel le code s'exécute. Accédez aux données à partir d’un objet de base de données CLR à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’aide de la .NET Framework fournisseur de données pour les données du client géré et des applications de couche intermédiaire. C'est la raison pour laquelle vous pouvez tirer parti de vos connaissances d'ADO.NET et de `SqlClient` dans les applications clientes managées et de couche intermédiaire.  
  
> [!NOTE]  
>  Les méthodes de type défini par l'utilisateur et les fonctions définies par l'utilisateur ne sont pas autorisées à effectuer un accès aux données par défaut. Vous devez définir la propriété `DataAccess` de `SqlMethodAttribute` ou `SqlFunctionAttribute` à `DataAccessKind.Read` pour permettre l'accès aux données en lecture seule à partir des méthodes de type défini par l'utilisateur ou des fonctions définies par l'utilisateur. Les opérations de modification des données ne sont pas autorisées à partir des types définis par l'utilisateur ou des fonctions définies par l'utilisateur ; par ailleurs, elles lèvent des exceptions au moment de l'exécution, à la moindre tentative.  
  
 Cette section décrit uniquement les différences spécifiques en matière de fonctionnement et de comportement lors de l'accès aux données à partir d'un objet de base de données CLR. Pour plus d'informations sur les fonctionnalités d'ADO.NET, consultez la documentation ADO.NET incluse dans le Kit de développement logiciel .NET Framework (SDK).  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Connexion contextuelle](context-connection.md)  
 Décrit la connexion contextuelle à SQL Server.  
  
 [Emprunt d'identité et informations d'identification pour les connexions](impersonation-and-credentials-for-connections.md)  
 Décrit l'emprunt d'identité et les informations d'identification des connexions.  
  
 [Extensions spécifiques in-process de SQL Server à ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Décrit les objets in-process `SqlPipe`, `SqlContext`, `SqlTriggerContext` et `SqlDataRecord` spécifiques.  
  
 [Intégration et transactions du CLR](../../native-client-ole-db-transactions/transactions.md)  
 Explique comment la nouvelle infrastructure de transaction fournie dans l'espace de noms System.Transactions s'intègre à ADO.NET et décrit l'intégration du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Sérialisation XML à partir d'objets de base de données CLR](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 Explique comment activer les scénarios de sérialisation XML des objets de base de données CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
