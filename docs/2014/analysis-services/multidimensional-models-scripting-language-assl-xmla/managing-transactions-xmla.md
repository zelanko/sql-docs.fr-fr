---
title: Gestion des transactions (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad8a77d1d8552dc811c1232afb53c142452658db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727206"
---
# <a name="managing-transactions-xmla"></a>Gestion des transactions (XMLA)
  Chaque commande XML for Analysis (XMLA) envoyée à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécute dans le contexte d’une transaction sur la session implicite ou explicite actuelle. Pour gérer chacune de ces transactions, vous devez utiliser les commandes [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) . En utilisant ces commandes, vous pouvez créer des transactions implicites ou explicites, modifier le nombre de références de transaction, ainsi que les transactions de démarrage, de validation ou d'annulation.  
  
## <a name="implicit-and-explicit-transactions"></a>Transactions implicites et explicites  
 Une transaction est soit implicite, soit explicite :  
  
 **Transaction implicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]crée une transaction *implicite* pour une commande XMLA si `BeginTransaction` la commande ne spécifie pas le début d’une transaction. 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide toujours une transaction implicite si la commande aboutit et l'annule si la commande échoue.  
  
 **Transaction explicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]crée une transaction *explicite* si la `BeginTransaction` commande démarre une transaction. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne valide une transaction explicite que si une commande `CommitTransaction` est envoyée et l'annule si une commande `RollbackTransaction` est envoyée.  
  
 De plus, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] annule les transactions implicites et explicites si la session active se termine avant que la transaction active n'ait abouti.  
  
## <a name="transactions-and-reference-counts"></a>Transactions et nombres de référence  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comptabilise le nombre de référence de transactions pour chaque session. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prend pas en charge les transactions imbriquées dans la mesure où une seule transaction active est gérée par session. Si aucune transaction n'est active dans la session active, le nombre de références de transaction est défini à zéro.  
  
 En d'autres termes, chaque commande `BeginTransaction` incrémente le nombre de références d'une unité, et chaque commande `CommitTransaction` décrémente le nombre de références d'une unité. Si une commande `CommitTransaction` définit le nombre de transactions à zéro, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction.  
  
 Cependant, la commande `RollbackTransaction` annule la transaction active quelle que soit la valeur actuelle du nombre de références de transaction. Autrement dit, une seule commande `RollbackTransaction` permet d'annuler la transaction active, quel que soit le nombre de commandes `BeginTransaction` ou `CommitTransaction` qui ont été envoyées, et définit le nombre de références de transaction à zéro.  
  
## <a name="beginning-a-transaction"></a>Lancement d'une transaction  
 La commande `BeginTransaction` lance une transaction explicite sur la session active et incrémente le nombre de référence de transactions correspondant d'une unité. Toutes les commandes suivantes sont considérées comme faisant partie de la transaction active, jusqu'à ce qu'un nombre suffisant de commandes `CommitTransaction` soit envoyé pour valider la transaction active ou qu'une commande unique `RollbackTransaction` soit envoyée pour annuler la transaction active.  
  
## <a name="committing-a-transaction"></a>Validation d'une transaction  
 La commande `CommitTransaction` valide les résultats des commandes exécutées après que la commande `BeginTransaction` a été exécutée sur la session active. Chaque commande `CommitTransaction` décrémente le nombre de référence pour les transactions actives d'une session. Si une commande `CommitTransaction` définit le nombre de références à zéro, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction active. En l'absence de toute transaction active (en d'autres termes, le nombre de référence de transactions pour la session active est déjà défini à zéro), une commande `CommitTransaction` provoque une erreur.  
  
## <a name="rolling-back-a-transaction"></a>Annulation d'une transaction  
 La commande `RollbackTransaction` annule les résultats des commandes exécutées après que la commande `BeginTransaction` a été exécutée sur la session active. La commande `RollbackTransaction` annule la transaction active, quel que soit le nombre de références de transaction actuel, et définit le nombre de références de transaction à zéro. En l'absence de toute transaction active (en d'autres termes, le nombre de référence de transactions pour la session active est déjà défini à zéro), une commande `RollbackTransaction` provoque une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
