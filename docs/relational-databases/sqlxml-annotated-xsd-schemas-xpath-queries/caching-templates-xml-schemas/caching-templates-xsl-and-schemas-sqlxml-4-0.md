---
title: Mise en cache des modèles, XSL et schémas (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6201cd2cf27e48f5a5101c3bdcda4da644756a13
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75246689"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Mise en cache des modèles, XSL et schémas (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Pour améliorer les performances, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 prend en charge la mise en cache des modèles, des fichiers XSL et des schémas.  
  
 Tous les schémas, modèles et fichiers XSL (à l’exception des fichiers à partir d’un emplacement https://ou ftp://) sont mis en cache. Les fichiers mis en cache demeurent en mémoire pendant que le processus est en cours d'exécution. Lorsque le processus s'arrête, la totalité du cache est perdue. Par conséquent, si vous exécutez un processus par requête, l'avantage de la mise en cache peut ne pas être perceptible.  
  
 Les rubriques de cette section fournissent plus d'informations sur la mise en cache.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mise en cache de modèle &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des modèles.  
  
 [Mise en cache XSL &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des fichiers XSL.  
  
 [Mise en cache de schéma &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 Explique les installations SQLXML côte à côte en rapport avec la mise en cache de schémas, et fournit les clés de Registre pour la mise en cache des schémas.  
  
  
