---
title: Types définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55db7c7c903f4b22a85f9762f13f845ea7ea17ba
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785444"
---
# <a name="user-defined-types"></a>Types définis par l’utilisateur

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les types définis par l'utilisateur (UDT, User-Defined Types) ont été introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] pour permettre à un développeur d'étendre le système de type scalaire du serveur en stockant des objets CLR (Common Language Runtime) dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les UDT peuvent contenir plusieurs éléments et avoir des comportements, contrairement aux types de données alias traditionnels qui ne comprennent qu'un seul type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Auparavant, les UDT étaient limités à une taille maximale de 8 kilo-octets. Dans [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], il existe désormais une prise en charge des types définis par l'utilisateur (UDT) supérieurs à 64 kilo-octets. La version 3.0 du pilote JDBC prend à présent également en charge les UDT supérieurs à 64 kilo-octets lorsque vous spécifiez le format UserDefined.

Il n'existe aucune modification du comportement pour les types définis par l'utilisateur (UDT) dont la taille est inférieure ou égale à 8 000 octets, mais les types définis par l'utilisateur plus volumineux sont pris en charge et affichent une taille « illimitée ».

## <a name="see-also"></a> Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
