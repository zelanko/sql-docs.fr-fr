---
title: access check cache (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0024a9d0f9999b372ff50d7144a23490529e472e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287895"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache (option de configuration de serveur)
  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]accède aux objets de base de données, la vérification de l'accès est mise en cache dans une structure interne appelée le **cache de résultat de la vérification d'accès**. Les options **access check cache quota** et **access check cache bucket count** contrôlent le nombre d'entrées et le nombre de compartiments de hachage utilisés pour le **cache de résultat de la vérification d'accès**. Dans de rares circonstances, la modification de ces options peut améliorer les performances.  
  
 Les valeurs par défaut 0 indiquent que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère ces options. Microsoft recommande de ne modifier ces options que sur recommandation du support technique.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
