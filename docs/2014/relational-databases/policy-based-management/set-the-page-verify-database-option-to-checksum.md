---
title: Définir l’option de base de données PAGE_VERIFY sur CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fe1a48e74503e93199a6e91f8b9aa60c21bb9ee1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62691529"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Définir l'option de base de données PAGE_VERIFY sur CHECKSUM
  Cette règle vérifie si l'option de base de données PAGE_VERIFY est définie sur la valeur CHECKSUM. Si CHECKSUM est activé pour l'option de base de données PAGE_VERIFY, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcule une somme de contrôle portant sur le contenu de la page toute entière et stocke la valeur obtenue dans l'en-tête de la page dès que cette dernière est écrite sur le disque. Lorsque la page est lue à partir du disque, la somme de contrôle est recalculée, puis comparée à la valeur de la somme de contrôle stockée dans l'en-tête de page. Cela permet d'obtenir un niveau élevé d'intégrité des fichiers de données.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option de base de données PAGE_VERIFY sur la valeur CHECKSUM.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
