---
title: Formes canoniques et restrictions de modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d5fb6b52893b4bd79220b1fb6ec5096350f387a7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249699"
---
# <a name="canonical-forms-and-pattern-restrictions"></a>Formes canoniques et restrictions de modèle
  La facette de modèle XSD permet la restriction de l'espace lexical des types simples. Quand une restriction de modèle est appliquée à un type pour lequel il existe plusieurs représentations lexicales possibles, certaines valeurs peuvent entraîner un comportement inattendu lors de la validation.  
  
 Ce comportement se produit car les représentations lexicales de ces valeurs ne sont pas stockées dans la base de données. Par conséquent, les valeurs sont converties en leurs représentations canoniques lorsqu'elles sont sérialisées pour la sortie. Si un document contient une valeur dont la forme canonique n'est pas conforme à la restriction de modèle propre à son type, il est rejeté si un utilisateur tente de réinsérer la valeur.  
  
 Pour empêcher cela, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette tout document XML comportant des valeurs ne pouvant pas être réinsérées, en raison de la violation des restrictions de modèle par leurs formes canoniques. Ainsi, la valeur « 33 000 » n’est pas validée par rapport à un type dérivé de **xs:decimal** ayant pour restriction de modèle « 33\\.0+ ». Bien que « 33 000 » soit conforme à ce modèle, la forme canonique, « 33 », elle, ne l'est pas.  
  
 Par conséquent, soyez prudent lorsque vous appliquez des facettes de modèles pour les types dérivés de types primitifs suivants : `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary` , et `base64Binary`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] émet un avertissement lorsque vous ajoutez de tels composants à une collection de schémas.  
  
 Une sérialisation imprécise de valeurs en virgule flottante donne lieu à un problème similaire. Du fait de l'algorithme de sérialisation en virgule flottante utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est possible pour des valeurs similaires de partager la même forme canonique. Quand une valeur en virgule flottante est sérialisée puis réinsérée, sa valeur peut varier légèrement. En de rares occasions, cela peut produire une valeur enfreignant l'une des facettes suivantes propres à son type au moment de sa réinsertion : **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**ou **maxExclusive**. Pour éviter ce problème, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette toutes les valeurs des types dérivés de `xs:float` ou de `xs:double` ne pouvant pas être sérialisées et réinsérées.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
