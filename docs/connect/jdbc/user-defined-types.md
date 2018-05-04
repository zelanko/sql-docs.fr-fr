---
title: Types définis par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3873e2d05eab1fb7ce0ec26db73a78ce1c39b28e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="user-defined-types"></a>Types définis par l’utilisateur
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Types définis par l’utilisateur (UDT) ont été introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] pour permettre à un développeur d’étendre le système de type scalaire du serveur en stockant l’objets du common language runtime (CLR) dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données. Les UDT peuvent contenir plusieurs éléments et avoir des comportements, contrairement aux types de données alias traditionnels, qui se composent d’un seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données système. Auparavant, les UDT étaient limités à une taille maximale de 8 kilo-octets. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], prise en charge a été ajoutée pour les UDT supérieurs à 64 kilo-octets. La version 3.0 du pilote JDBC prend à présent également en charge les UDT supérieurs à 64 kilo-octets lorsque vous spécifiez le format UserDefined.  
  
 Il n'existe aucune modification du comportement pour les types définis par l'utilisateur (UDT) dont la taille est inférieure ou égale à 8 000 octets, mais les types définis par l'utilisateur plus volumineux sont pris en charge et affichent une taille « illimitée ».  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
