---
title: Mise en cache des modèles, XSL et schémas (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82b943a170c42010b650033841f6612338d99119
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013252"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Mise en cache des modèles, XSL et schémas (SQLXML 4.0)
  Pour améliorer les performances, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 prend en charge la mise en cache des modèles, des fichiers XSL et des schémas.  
  
 Tous les schémas, modèles et fichiers XSL (sauf les fichiers provenant d'un emplacement http:// ou ftp://) sont mis en cache. Les fichiers mis en cache demeurent en mémoire pendant que le processus est en cours d'exécution. Lorsque le processus s'arrête, la totalité du cache est perdue. Par conséquent, si vous exécutez un processus par requête, l'avantage de la mise en cache peut ne pas être perceptible.  
  
 Les rubriques de cette section fournissent plus d'informations sur la mise en cache.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mise en cache de modèle &#40;SQLXML 4,0&#41;](template-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des modèles.  
  
 [Mise en cache XSL &#40;SQLXML 4,0&#41;](xsl-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des fichiers XSL.  
  
 [Mise en cache de schéma &#40;SQLXML 4,0&#41;](schema-caching-sqlxml-4-0.md)  
 Explique les installations SQLXML côte à côte en rapport avec la mise en cache de schémas, et fournit les clés de Registre pour la mise en cache des schémas.  
  
  
