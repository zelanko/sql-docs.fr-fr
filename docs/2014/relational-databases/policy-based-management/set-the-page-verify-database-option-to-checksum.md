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
ms.openlocfilehash: 13296a976722390668b8ca6d901cf0dd080e5cc3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066658"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Définir l'option de base de données PAGE_VERIFY sur CHECKSUM
  Cette règle vérifie si l'option de base de données PAGE_VERIFY est définie sur la valeur CHECKSUM. Si CHECKSUM est activé pour l'option de base de données PAGE_VERIFY, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcule une somme de contrôle portant sur le contenu de la page toute entière et stocke la valeur obtenue dans l'en-tête de la page dès que cette dernière est écrite sur le disque. Lorsque la page est lue à partir du disque, la somme de contrôle est recalculée, puis comparée à la valeur de la somme de contrôle stockée dans l'en-tête de page. Cela permet d'obtenir un niveau élevé d'intégrité des fichiers de données.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option de base de données PAGE_VERIFY sur la valeur CHECKSUM.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
