---
title: Instructions et limitations de SQLXML 4,0 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015386"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>Recommandations et limitations de SQLXML 4.0
  Gardez en mémoire les points suivants lors de l'utilisation de SQLXML 4.0 :  
  
-   Le XML retourné en tant que résultat de requête n'est pas validé par rapport au schéma de mappage qui a généré le XML.  
  
-   SQLXML 4.0 inclut des PROGID dépendants et indépendants de la version. Il est recommandé que toutes les applications de production utilisent des PROGID dépendants de la version. Ceci est tout particulièrement important car SQLXML 4.0 n'a pas une compatibilité descendante complète. L'utilisation de PROGID dépendant de la version offre une protection contre les échecs de production éventuels lors de l'installation de versions plus récentes. De version en version, le comportement du programme peut changer pour de multiples raisons comme la résolution de bogues, les modifications de conception, etc. L'utilisation de PROGID dépendants de la version offre une protection contre les échecs inattendus de l'installation de versions plus récentes. Avec des PROGID dépendants de la version, lorsque vous installez une version plus récente, votre application continuera de fonctionner sans échec. Si vous décidez de modifier les précédents PROGID dépendants de la version pour en utiliser de plus récents dans une nouvelle version, vous devez tester votre application avant de la mettre en production. Par exemple, les applications qui utilisent des PROGID indépendants de la version peuvent échouer dans le scénario suivant :  
  
     Vous exécutez une application qui utilise SQLXML 4.0 et des PROGID indépendants de la version, et vous décidez d'installer un autre programme. Ce programme peut installer une version antérieure de SQLXML. Votre application risque d'échouer car les PROGID indépendants de la version de votre application pointent maintenant vers la version antérieure de SQLXML, qui peut ou non avoir la fonctionnalité SQLXML utilisée par votre application.  
  
-   Si, pour une raison quelconque, vous ne souhaitez pas utiliser le fournisseur SQLXMLOLEDB et que vous souhaitez plutôt utiliser le fournisseur SQLOLEDB pour les fonctionnalités SQLXML, définissez la propriété **SQLXML Version** sur « SQLXML. 4.0 ».  
  
  
