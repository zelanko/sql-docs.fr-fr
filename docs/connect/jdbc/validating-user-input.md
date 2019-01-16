---
title: Validation des entrées utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24eef3e97f87d60db624605b19420e5fd562360b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213778"
---
# <a name="validating-user-input"></a>Validation de l'entrée utilisateur

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Lorsque vous construisez une application qui accède à des données, vous devez assumer que toutes les entrées utilisateur sont malveillantes jusqu'à preuve du contraire. Dans le cas contraire, vous risquez d'exposer votre application à des attaques. L’un des types d’attaques qui peuvent survenir porte le nom d’injection SQL ; du code malveillant est ajouté à des chaînes qui sont passées ultérieurement à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à des fins d’analyse et d’exécution. Pour éviter ce type d'attaque, vous devez utiliser des procédures stockées avec des paramètres dans la mesure du possible, et toujours valider l'entrée d'utilisateur.

La validation de l'entrée utilisateur dans le code client est importante afin de ne pas gaspiller d'allers-retours vers le serveur. Il est également important de valider les paramètres des procédures stockées sur le serveur afin d'intercepter les entrées non valides et qui contournent la validation côté client.

Pour plus d’informations sur l’injection SQL et sur la façon de l’éviter, consultez la rubrique relative à l’injection SQL dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la validation des paramètres de procédure stockée, consultez « Procédures stockées ([!INCLUDE[ssDE](../../includes/ssde_md.md)]) » et les rubriques subalternes dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a> Voir aussi

[Sécurisation des applications de pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)
