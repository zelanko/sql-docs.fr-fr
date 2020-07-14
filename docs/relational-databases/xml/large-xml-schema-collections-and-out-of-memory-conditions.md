---
title: Mémoire insuffisante avec les collections de schémas XML volumineuses | Microsoft Docs
description: Découvrez les solutions de gestion des conditions de mémoire insuffisante lors du chargement ou de la suppression d’une collection de schémas XML volumineuse.
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: d41a1899f496056af6c98b123decacf5357ef361
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738418"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Collections de schémas XML volumineuses et conditions de mémoire insuffisante
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Lors d'un appel à la fonction intégrée XML_SCHEMA_NAMESPACE() sur une collection de schémas XML de grande taille ou si vous tentez de supprimer une telle collection, une condition de mémoire insuffisante peut se produire. Pour pallier ce problème, envisagez les solutions suivantes :  
  
-   Si la charge imposée au système est faible, utilisez la commande DROP_XML_SCHEMA_COLLECTION. Si cette mesure ne permet pas de résoudre le problème, placez la base de données en mode mono-utilisateur à l'aide de l'instruction ALTER DATABASE et réexécutez DROP XML SCHEMA COLLECTION. Si la collection de schémas XML existe dans **master**, **model**ou **tempdb**, un redémarrage du serveur est requis pour passer en mode mono-utilisateur.  
  
-   Quand vous appelez XML_SCHEMA_NAMESPACE, essayez d'extraire un espace de noms de schéma XML, tentez l'appel à un moment où la charge système est moindre ou alors en mode mono-utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
