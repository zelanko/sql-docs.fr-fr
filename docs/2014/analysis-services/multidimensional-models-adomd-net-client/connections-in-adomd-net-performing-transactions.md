---
title: Exécution de Transactions dans ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04157786e3a3d9349c2f1e324291a3a0bda5928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167591"
---
# <a name="performing-transactions-in-adomdnet"></a>Exécution de transactions dans ADOMD.NET
  Dans ADOMD.NET, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> permet de gérer le contexte de transaction pour un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> donné. Ces fonctionnalités vous permettent d'exécuter plusieurs commandes dans le même contexte. Chaque commande lit les mêmes données sans que les données lues ne soient modifiées entre chaque exécution de commande.  
  
> [!NOTE]  
>  La classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> est l'implémentation de l'interface `System.Data.IDbTransaction`, qui fait partie intégrante de la bibliothèque de classes [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework et qui est implémentée par tous les fournisseurs de données .NET Framework qui prennent en charge les transactions.  
  
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
 [Établissement de connexions dans ADOMD.NET](connections-in-adomd-net.md)   
 [Programmation du client ADOMD.NET](adomd-net-client-programming.md)  
  
  
