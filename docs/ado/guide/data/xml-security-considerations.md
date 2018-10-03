---
title: Considérations de sécurité XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e80a0bbb70a626ff01043592896ecfbe3c21f189
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802879"
---
# <a name="xml-security-considerations"></a>Considérations relatives à la sécurité de XML
ADO enregistrer les méthodes Open sur l’objet Recordset ne sont pas considérés comme des opérations sécurisées avec Internet Explorer. Par conséquent, si ces méthodes sont utilisées dans un code de script qui s’exécute dans une application ou un contrôle qui est hébergé dans un navigateur, la configuration de sécurité du navigateur aura un effet sur son comportement.  
  
 Internet Explorer 5 fournit des restrictions de sécurité pour ces opérations par défaut dans les zones Internet. Avec cette configuration, le jeu d’enregistrements ne peut pas rendre tout accès au système de fichiers local sur le client ou accéder aux sources de données en dehors du domaine du serveur à partir duquel la page a été téléchargée. En particulier, lors de l’exécution à l’intérieur de l’hôte du navigateur, un jeu d’enregistrements peut enregistrée dans un fichier uniquement s’il est sur le même serveur à partir duquel la page a été téléchargée. De même, vous pouvez ouvrir un jeu d’enregistrements en le chargeant à partir d’un fichier uniquement si ce fichier se trouve sur le même serveur à partir duquel la page a été téléchargée.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
