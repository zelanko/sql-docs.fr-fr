---
title: "Méthode setPacketSize (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9684140ed084cc7a096675935ceec81209f8fa66
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Méthode setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la taille du paquet réseau actuelle utilisée pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], spécifié en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *packetSize*  
  
 Un **int** valeur contenant la taille du paquet réseau.  
  
## <a name="remarks"></a>Notes  
 La plage acceptable de valeurs de cette propriété est [-1 | 0 | 512..32767]. Si cette propriété est définie sur une valeur située en dehors des limites acceptables, une exception se produit.  
  
 L'application peut souhaiter définir la propriété packetSize pendant la connexion à l'aide du chiffrement SSL (Secure Sockets Layer). Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] négocie la taille du paquet avec le serveur. Si la propriété encrypt a la valeur «**true**» et la taille négociée du paquet est supérieure à la taille d’enregistrement du fournisseur de sécurité par défaut la Machine virtuelle Java (JVM) de SSL, le pilote génère une erreur et l’arrête.  
  
 De plus, l'application peut souhaiter définir la propriété packetSize sans demander de chiffrement SSL. Dans ce cas, si le serveur requiert que le client prenne en charge le chiffrement SSL, le pilote vérifie la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java. Si la propriété packetSize est supérieure à la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java, le pilote génère une erreur et met fin à la connexion.  
  
 Pour plus d’informations sur l’utilisation de SSL, consultez [le chiffrement SSL à l’aide de](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

