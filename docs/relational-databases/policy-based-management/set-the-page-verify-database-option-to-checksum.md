---
title: Définir l’option de base de données PAGE_VERIFY sur CHECKSUM | Microsoft Docs
description: Vérifiez si l'option PAGE_VERIFY est CHECKSUM, ce qui contrôle si le moteur de base de données de Microsoft SQL Server calcule une somme de contrôle pour aider à assurer l'intégrité des fichiers de données.
ms.custom: ''
ms.date: 08/19/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4dda2b9138882490b1556b9dbb39f71e35767f5f
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646509"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a>Définir l'option de base de données PAGE_VERIFY sur CHECKSUM
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie si l'option de base de données PAGE_VERIFY est définie sur la valeur CHECKSUM. Si CHECKSUM est activé pour l'option de base de données PAGE_VERIFY, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calcule une somme de contrôle portant sur le contenu de la page toute entière et stocke la valeur obtenue dans l'en-tête de la page dès que cette dernière est écrite sur le disque. Lorsque la page est lue à partir du disque, la somme de contrôle est recalculée, puis comparée à la valeur de la somme de contrôle stockée dans l'en-tête de page. Cela permet d'obtenir un niveau élevé d'intégrité des fichiers de données.  Si vous utilisez l’option PAGE VERIFY CHECKSUM pour une base de données, quand SQL Server repère qu’une page a été modifiée après avoir été écrite sur le disque, SQL Server présente le [message 824](../errors-events/mssqlserver-824-database-engine-error.md) après avoir relu la page sur le disque. 
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option de base de données PAGE_VERIFY sur la valeur CHECKSUM. L’utilisation de l’option de base de données PAGE_VERIFY CHECKSUM est celle qui permet le mieux de détecter les problèmes de cohérence de base de données causés par le chemin d’E/S système.
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
