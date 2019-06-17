---
title: Gestion des Transactions (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c85b1f9db4667c64bed7cf87189e48b507e5f75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63055074"
---
# <a name="managing-transactions-xmla"></a>Gestion des transactions (XMLA)
  Chaque commande XML for Analysis (XMLA) envoyé à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’exécute dans le contexte d’une transaction sur la session implicite ou explicite active. Pour gérer chacune de ces transactions, vous utilisez le [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) commandes. En utilisant ces commandes, vous pouvez créer des transactions implicites ou explicites, modifier le nombre de références de transaction, ainsi que les transactions de démarrage, de validation ou d'annulation.  
  
## <a name="implicit-and-explicit-transactions"></a>Transactions implicites et explicites  
 Une transaction est soit implicite, soit explicite :  
  
 **Transaction implicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Crée un *implicite* transaction pour un XMLA commande si le **BeginTransaction** commande ne spécifie pas le démarrage d’une transaction. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide toujours une transaction implicite si la commande aboutit et l'annule si la commande échoue.  
  
 **Transaction explicite**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Crée un *explicite* transaction si le **BeginTransaction** commande démarre une transaction. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne valide une transaction explicite si une **CommitTransaction** commande est envoyée et restaure une transaction explicite si une **RollbackTransaction** commande est envoyée.  
  
 De plus, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] annule les transactions implicites et explicites si la session active se termine avant que la transaction active n'ait abouti.  
  
## <a name="transactions-and-reference-counts"></a>Transactions et nombres de référence  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comptabilise le nombre de référence de transactions pour chaque session. Toutefois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prend pas en charge les transactions imbriquées dans la mesure où une seule transaction active est gérée par session. Si aucune transaction n'est active dans la session active, le nombre de références de transaction est défini à zéro.  
  
 En d’autres termes, chaque **BeginTransaction** commande incrémente le décompte de références d’une unité, tandis que chaque **CommitTransaction** commande décrémente le décompte références d’une unité. Si un **CommitTransaction** à zéro, la commande définit le nombre de transactions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction.  
  
 Toutefois, le **RollbackTransaction** commande restaure la transaction active quelle que soit la valeur actuelle du décompte de références de transaction. En d’autres termes, une seule **RollbackTransaction** commande restaure la transaction active, quel que soit le nombre **BeginTransaction** commandes ou **CommitTransaction** les commandes ont été envoyés et définit le nombre de références de transaction à zéro.  
  
## <a name="beginning-a-transaction"></a>Lancement d'une transaction  
 Le **BeginTransaction** commande démarre une transaction explicite dans la session active et incrémente le décompte de références de transaction pour la session active d’une unité. Toutes les commandes suivantes sont considérées comme au sein de la transaction active, jusqu'à ce que suffisamment **CommitTransaction** commandes sont envoyées à valider la transaction active ou un seul **RollbackTransaction**commande est envoyée pour restaurer la transaction active.  
  
## <a name="committing-a-transaction"></a>Validation d'une transaction  
 Le **CommitTransaction** commande valide les résultats des commandes exécutées après que le **BeginTransaction** commande a été exécutée sur la session active. Chaque **CommitTransaction** commande décrémente le décompte de références pour les transactions actives sur une session. Si un **CommitTransaction** à zéro, la commande définit le nombre de références [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] valide la transaction active. S’il n’existe aucune transaction active (en d’autres termes, le décompte de références de transaction pour la session active est déjà défini à zéro), un **CommitTransaction** commande entraîne une erreur.  
  
## <a name="rolling-back-a-transaction"></a>Annulation d'une transaction  
 Le **RollbackTransaction** commande restaure les résultats des commandes exécutées après que le **BeginTransaction** commande a été exécutée sur la session active. Le **RollbackTransaction** commande restaure la transaction active, quel que soit le nombre de références de la transaction actuelle et définit le nombre de références de transaction à zéro. S’il n’existe aucune transaction active (en d’autres termes, le décompte de références de transaction pour la session active est déjà défini à zéro), un **RollbackTransaction** commande entraîne une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
