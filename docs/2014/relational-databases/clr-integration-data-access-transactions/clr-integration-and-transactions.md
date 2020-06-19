---
title: Intégration et transactions du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955052"
---
# <a name="clr-integration-and-transactions"></a>Intégration et transactions du CLR
  L'espace de noms `System.Transactions` fournit une infrastructure de transaction qui s'intègre entièrement à ADO.NET et au CLR (Common Language Runtime) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. `System.Transactions` et ADO.NET fonctionnent conjointement pour étendre et simplifier l'utilisation de transactions locales et distribuées dans les applications managées.  
  
> [!NOTE]  
>  Une procédure CLR définie par l'utilisateur ne peut ni établir de connexion au serveur sur lequel elle s'exécute (connexion de bouclage) ni s'inscrire dans la même transaction. Si cette opération est tentée, la tentative de connexion est bloquée et le contrôle n'est pas redonné à la procédure définie par l'utilisateur. Il en résulte une erreur de délai d'attente (Msg 1206) sur la procédure définie par l'utilisateur.  
  
 Pour plus d'informations sur les transactions et le .NET Framework, consultez les rubriques relatives à l'exécution de transactions et à l'exploitation de transactions dans le Kit de développement logiciel (SDK) .NET Framework.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Promotion des transactions](transaction-promotion.md)  
 Décrit la possibilité de promouvoir des transactions et l'utilisation de cette fonctionnalité.  
  
 [Accès à la transaction actuelle](accessing-the-current-transaction.md)  
 Décrit comment accéder à une transaction en cours d'exécution in-process sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Utilisation de System.Transactions](../native-client-ole-db-transactions/transactions.md)  
 Décrit comment utiliser l'interface de programmation d'applications (API) `System.Transactions` dans votre application managée.  
  
 [Durées de vie des transactions](transaction-lifetimes.md)  
 Décrit la différence en termes de durée de vie entre les transactions démarrées dans les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] et celles démarrées dans les applications CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données à partir d'objets de base de données CLR](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
