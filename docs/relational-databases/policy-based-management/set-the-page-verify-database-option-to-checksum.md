---
title: Définir l’option de base de données PAGE_VERIFY sur CHECKSUM | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 20f97815b85b7cf88baad386bda43596c5ac81a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784627"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>Définir l'option de base de données PAGE_VERIFY sur CHECKSUM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie si l'option de base de données PAGE_VERIFY est définie sur la valeur CHECKSUM. Si CHECKSUM est activé pour l'option de base de données PAGE_VERIFY, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcule une somme de contrôle portant sur le contenu de la page toute entière et stocke la valeur obtenue dans l'en-tête de la page dès que cette dernière est écrite sur le disque. Lorsque la page est lue à partir du disque, la somme de contrôle est recalculée, puis comparée à la valeur de la somme de contrôle stockée dans l'en-tête de page. Cela permet d'obtenir un niveau élevé d'intégrité des fichiers de données.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option de base de données PAGE_VERIFY sur la valeur CHECKSUM.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
