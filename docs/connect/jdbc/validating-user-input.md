---
title: "Validation des entrées utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a00eafc9f72910f05c1850b25bba5e91a4e276a6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="validating-user-input"></a>Validation de l'entrée utilisateur
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous construisez une application qui accède à des données, vous devez assumer que toutes les entrées utilisateur sont malveillantes jusqu'à preuve du contraire. Dans le cas contraire, vous risquez d'exposer votre application à des attaques. Un type d’attaque peut se produire est appelé d’injection SQL, où un code malveillant est ajouté aux chaînes transmises ultérieurement à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour être analysé et exécuté. Pour éviter ce type d'attaque, vous devez utiliser des procédures stockées avec des paramètres dans la mesure du possible, et toujours valider l'entrée d'utilisateur.  
  
 La validation de l'entrée utilisateur dans le code client est importante afin de ne pas gaspiller d'allers-retours vers le serveur. Il est également important de valider les paramètres des procédures stockées sur le serveur afin d'intercepter les entrées non valides et qui contournent la validation côté client.  
  
 Pour plus d’informations sur l’injection SQL et comment l’éviter, consultez la rubrique « SQL Injection » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] la documentation en ligne. Pour plus d’informations sur la validation des paramètres de procédure stockée, consultez « procédures stockées ([!INCLUDE[ssDE](../../includes/ssde_md.md)]) » et les rubriques subalternes dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications de pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
