---
title: Comprendre le verrouillage de ligne | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7b41b33aa022bc0a62996e09a713f36bbe04e816
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-row-locking"></a>Présentation du verrouillage de ligne
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] verrous de ligne. Ces verrous implémentent le contrôle de concurrence entre plusieurs utilisateurs qui effectuent simultanément des modifications dans une base de données. Par défaut, les transactions et verrous sont gérés sur la base de chaque connexion. Par exemple, si une application ouvre deux connexions JDBC, les verrous acquis par une connexion ne peuvent pas être partagés avec l'autre connexion. Aucune connexion ne peut acquérir des verrous qui seraient en conflit avec les verrous détenus par l'autre connexion.  
  
> [!NOTE]  
>  Si le verrouillage de ligne est utilisé, toutes les lignes dans la mémoire tampon d'extraction sont verrouillées ; par conséquent, un très grand paramètre pour la taille d'extraction peut affecter la concurrence.  
  
 Le verrouillage est utilisé pour garantir l'intégrité transactionnelle et la cohérence de base de données. Le verrouillage empêche les utilisateurs de lire des données qui sont en cours de modification par d'autres utilisateurs et empêche plusieurs utilisateurs de modifier simultanément les mêmes données. Si le verrouillage n'est pas utilisé, les données dans la base de données peuvent devenir logiquement incorrectes et les requêtes exécutées contre ces données peuvent produire des résultats inattendus.  
  
> [!NOTE]  
>  Pour plus d’informations sur le verrouillage de ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], consultez « verrouillage dans le [!INCLUDE[ssDE](../../includes/ssde_md.md)]» dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Résultat de la gestion des jeux avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  

