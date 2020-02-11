---
title: Promotion de la transaction | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
author: rothja
ms.author: jroth
ms.openlocfilehash: d75bbf1c4d468a0d6c3872a220566d667b059a5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937500"
---
# <a name="transaction-promotion"></a>Promotion des transactions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La *promotion* des transactions décrit une transaction locale légère qui peut être promue automatiquement en une transaction entièrement distribuable si nécessaire. Lorsqu'une procédure stockée managée est appelée au sein d'une transaction de base de données sur le serveur, le CLR s'exécute dans le contexte d'une transaction locale.  Si une connexion à un serveur distant est ouverte dans une transaction de base de données, la connexion au serveur distant est inscrite dans la transaction distribuée et la transaction locale est promue automatiquement en une transaction distribuée. Ainsi, la promotion des transactions réduit les charges mémoire des transactions distribuées en différant la création d'une transaction distribuée tant qu'elle n'est pas nécessaire. La promotion des transactions est automatique, si elle a été activée à l'aide du mot clé **Enlist** , et ne requiert aucune intervention du développeur. Le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assure la prise en charge de la promotion des transactions au travers des classes de l'espace de noms **System.Data.SqlClient** du .NET Framework.  
  
## <a name="the-enlist-keyword"></a>Mot clé Enlist  
 La propriété **ConnectionString** d'un objet **SqlConnection** prend en charge le mot clé **Enlist** , qui indique si **System.Data.SqlClient** détecte les contextes transactionnels et inscrit automatiquement la connexion dans une transaction distribuée. Si le mot clé est défini avec la valeur true (valeur par défaut), la connexion est automatiquement inscrite dans le contexte de transaction actif du thread d'ouverture. S'il est défini avec la valeur false, la connexion SqlClient n'interagit pas avec une transaction distribuée. Si **Enlist** n'est pas spécifié dans la chaîne de connexion, la connexion est inscrite automatiquement dans une transaction distribuée si celle-ci est détectée au moment où la connexion est ouverte.  
  
## <a name="distributed-transactions"></a>Transactions distribuées  
 Les transactions distribuées consomment en général d'importantes ressources système. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) gère ces transactions et intègre tous les gestionnaires de ressources qui y sont accédés. La promotion des transactions, en revanche, est une forme spéciale de transaction **System.Transactions** qui délègue efficacement le travail à une simple transaction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **System. transactions**, **System. Data. SqlClient**et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordonnent le travail impliqué dans la gestion de la transaction, en la promouvant en une transaction distribuée complète en fonction des besoins.  
  
 L'avantage de l'utilisation de la promotion des transaction est que lorsqu'une connexion est ouverte avec une transaction **TransactionScope** active et qu'aucune autre connexion n'est ouverte, la transaction est validée comme transaction légère, au lieu d'encourir les charges mémoire supplémentaires d'une transaction distribuée complète. Pour plus d’informations sur **TransactionScope**, consultez [utilisation de System. transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration et transactions du CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
