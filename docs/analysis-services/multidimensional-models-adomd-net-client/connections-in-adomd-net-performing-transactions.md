---
title: "Exécution de Transactions dans ADOMD.NET | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b7fe4d80598e56de50748fd53e651ca1a2b5a48b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="connections-in-adomdnet---performing-transactions"></a>Connexions dans ADOMD.NET - exécution de Transactions
  Dans ADOMD.NET, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> permet de gérer le contexte de transaction pour un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> donné. Ces fonctionnalités vous permettent d'exécuter plusieurs commandes dans le même contexte. Chaque commande lit les mêmes données sans que les données lues ne soient modifiées entre chaque exécution de commande.  
  
> [!NOTE]  
>  Le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> classe est l’implémentation de la **System.Data.IDbTransaction** interface, une partie de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] bibliothèque de classes .NET Framework et implémentée par tous les fournisseurs de données .NET Framework qui prennent en charge des transactions.  
  
 L'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> ne prend en charge que les transactions validées en lecture, dans lesquelles les verrous partagés sont maintenus pendant la lecture des données afin d'éviter des lectures erronées.  
  
 L'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> est utilisée pour démarrer la transaction. Pour utiliser la transaction, des commandes sont ensuite exécutées sur la connexion qui a démarré la transaction. Une fois que vous avez terminé la transaction, vous pouvez soit l'annuler, soit la valider.  
  
## <a name="starting-a-transaction"></a>Démarrage d'une transaction  
 Vous pouvez créer une instance d'un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> en appelant la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. L'exemple suivant montre comment créer une instance de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> :  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>Annulation d'une transaction  
 Pour annuler une transaction incomplète existante, vous devez appeler la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Si vous appelez cette méthode pour une transaction complète existante, une exception est levée.  
  
## <a name="committing-a-transaction"></a>Validation d'une transaction  
 Après avoir appelé la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> pour démarrer une transaction, vous pouvez terminer la transaction en appelant la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Si cette méthode est appelée pour une transaction complète existante, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [Établissement de connexions dans ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)   
 [Programmation du Client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
