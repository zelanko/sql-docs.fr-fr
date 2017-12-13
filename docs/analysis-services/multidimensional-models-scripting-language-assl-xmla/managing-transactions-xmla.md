---
title: Gestion des Transactions (XMLA) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3c61c2edfbc6b2fad49a5d7e08dced6cbffe6673
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="managing-transactions-xmla"></a>Gestion des transactions (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Chaque commande XML for Analysis (XMLA) envoyé à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécute dans le contexte d’une transaction sur la session implicite ou explicite. Pour gérer chacune de ces transactions, vous utilisez la [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), et [RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) commandes. En utilisant ces commandes, vous pouvez créer des transactions implicites ou explicites, modifier le nombre de références de transaction, ainsi que les transactions de démarrage, de validation ou d'annulation.  
  
## <a name="implicit-and-explicit-transactions"></a>Transactions implicites et explicites  
 Une transaction est soit implicite, soit explicite :  
  
 **Transaction implicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Crée un *implicite* transaction pour XMLA : une commande si le **BeginTransaction** commande ne spécifie pas le début d’une transaction. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide toujours une transaction implicite si la commande aboutit et l'annule si la commande échoue.  
  
 **Transaction explicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Crée un *explicite* transaction si le **BeginTransaction** commande démarre une transaction. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne valide une transaction explicite si un **CommitTransaction** commande est envoyée et annule une transaction explicite si un **RollbackTransaction** commande est envoyée.  
  
 De plus, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] annule les transactions implicites et explicites si la session active se termine avant que la transaction active n'ait abouti.  
  
## <a name="transactions-and-reference-counts"></a>Transactions et nombres de référence  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comptabilise le nombre de référence de transactions pour chaque session. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prend pas en charge les transactions imbriquées dans la mesure où une seule transaction active est gérée par session. Si aucune transaction n'est active dans la session active, le nombre de références de transaction est défini à zéro.  
  
 En d’autres termes, chaque **BeginTransaction** commande incrémente le décompte de références d’une unité, tandis que chaque **CommitTransaction** décrémente commande le décompte de références d’une unité. Si un **CommitTransaction** à zéro, la commande définit le nombre de transactions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction.  
  
 Toutefois, le **RollbackTransaction** commande restaure la transaction active quelle que soit la valeur actuelle du décompte de références de transaction. En d’autres termes, un seul **RollbackTransaction** commande restaure la transaction active, quel que soit le nombre **BeginTransaction** commandes ou **CommitTransaction** commandes ont été envoyées, et les jeux de décompte de référence de la transaction à zéro.  
  
## <a name="beginning-a-transaction"></a>Lancement d'une transaction  
 Le **BeginTransaction** commande démarre une transaction explicite dans la session active et incrémente le décompte de références de transaction pour la session en cours d’une unité. Toutes les commandes suivantes sont considérés comme étant dans la transaction active, jusqu'à ce que suffisamment **CommitTransaction** commandes sont envoyées à valider la transaction active ou une seule **RollbackTransaction** commande est envoyée pour restaurer la transaction active.  
  
## <a name="committing-a-transaction"></a>Validation d'une transaction  
 Le **CommitTransaction** commande valide les résultats des commandes exécutées après que le **BeginTransaction** commande a été exécutée sur la session active. Chaque **CommitTransaction** commande décrémente le décompte de références pour les transactions actives sur une session. Si un **CommitTransaction** à zéro, la commande définit le nombre de références [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction active. S’il n’existe aucune transaction active (en d’autres termes, le nombre de références de transaction pour la session active est déjà défini à zéro), un **CommitTransaction** commande génère une erreur.  
  
## <a name="rolling-back-a-transaction"></a>Annulation d'une transaction  
 Le **RollbackTransaction** commande restaure les résultats des commandes exécutées après que le **BeginTransaction** commande a été exécutée sur la session active. Le **RollbackTransaction** commande restaure la transaction active, quel que soit le nombre de références de la transaction actuelle et définit le nombre de références de transaction à zéro. S’il n’existe aucune transaction active (en d’autres termes, le nombre de références de transaction pour la session active est déjà défini à zéro), un **RollbackTransaction** commande génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
