---
description: Considérations relatives à la sécurité de XML
title: Considérations relatives à la sécurité XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: rothja
ms.author: jroth
ms.openlocfilehash: 608ad67d531573d0124ea312252e6d30c289bf15
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978790"
---
# <a name="xml-security-considerations"></a>Considérations relatives à la sécurité de XML
Les méthodes ADO Save et Open sur l’objet Recordset ne sont pas considérées comme des opérations sécurisées pour s’exécuter dans Internet Explorer. Ainsi, si ces méthodes sont utilisées dans un code de script qui s’exécute dans une application ou un contrôle hébergé dans un navigateur, la configuration de la sécurité du navigateur aura un effet sur son comportement.  
  
 Internet Explorer 5 fournit des restrictions de sécurité pour ces opérations par défaut dans les zones Internet. Dans cette configuration, le jeu d’enregistrements ne peut pas accéder au système de fichiers local sur le client ou accéder à des sources de données situées en dehors du domaine du serveur à partir duquel la page a été téléchargée. Plus précisément, lors de l’exécution au sein de l’hôte du navigateur, un jeu d’enregistrements peut être enregistré dans un fichier uniquement s’il se trouve sur le même serveur que celui à partir duquel la page a été téléchargée. De même, vous pouvez ouvrir un Recordset en le chargeant à partir d’un fichier uniquement si ce fichier se trouve sur le même serveur que celui à partir duquel la page a été téléchargée.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](./persisting-records-in-xml-format.md)