---
title: access check cache (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158757"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache (option de configuration de serveur)
Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]accède aux objets de base de données, la vérification de l'accès est mise en cache dans une structure interne appelée le **cache de résultat de la vérification d'accès**. 
  
L’option de **nombre de compartiments du cache de vérification d’accès** contrôle le nombre de compartiments de hachage utilisés pour le cache des résultats de la vérification d’accès. 

L’option de **quota de vérification du cache d’accès** contrôle le nombre d’entrées stockées dans le cache des résultats de la vérification d’accès. Lorsque le nombre maximal d’entrées est atteint, les entrées les plus anciennes sont supprimées du cache des résultats de la vérification d’accès.
  
Les valeurs par défaut 0 indiquent que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère ces options. À partir de [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , les valeurs par défaut sont converties en configurations internes suivantes :
-   Pour la vérification d’accès nombre de compartiments du cache, la valeur 0 définit une valeur par défaut de 256 compartiments pour l’architecture x86 et 2 048 compartiments pour les architectures x64 et IA-64.
-   Pour le quota de vérification d’accès du cache, la valeur 0 définit une valeur par défaut de 1 024 entrées pour l’architecture x86 et 28 192 048 compartiments pour les architectures x64 et IA-64.

Dans de rares circonstances, la modification de ces options peut améliorer les performances. Par exemple, vous souhaiterez peut-être réduire la taille du cache des résultats de la vérification d’accès si la quantité de mémoire utilisée est trop importante. Ou bien, vous souhaiterez peut-être augmenter la taille du cache des résultats de la vérification d’accès si vous constatez une utilisation intensive du processeur lorsque les autorisations sont recalculées.

> [!IMPORTANT]
> Microsoft recommande de ne modifier ces options que sur recommandation du support technique.
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
