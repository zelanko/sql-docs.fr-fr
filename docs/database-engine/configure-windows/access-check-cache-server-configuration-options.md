---
title: access check cache (option de configuration de serveur) | Microsoft Docs
description: Découvrez le cache des résultats de la vérification d’accès et les options qui contrôlent le comportement du cache. Découvrez quand modifier ces options dans SQL Server.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a389b84e673315a3c27f44c68a80092bf739d94b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751195"
---
# <a name="access-check-cache-server-configuration-options"></a>access check cache (option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]accède aux objets de base de données, la vérification de l'accès est mise en cache dans une structure interne appelée le **cache de résultat de la vérification d'accès**. Les options **access check cache quota** et **access check cache bucket count** contrôlent le nombre d'entrées et le nombre de compartiments de hachage utilisés pour le **cache de résultat de la vérification d'accès**. Dans de rares circonstances, la modification de ces options peut améliorer les performances.  
  
 Les valeurs par défaut 0 indiquent que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère ces options. Microsoft recommande de ne modifier ces options que sur recommandation du support technique.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
