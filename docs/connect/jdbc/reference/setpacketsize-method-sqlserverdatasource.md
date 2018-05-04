---
title: Méthode setPacketSize (SQLServerDataSource) | Documents Microsoft
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
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab0f7cff0547fd5ea66fdbab192547ae7e82dbe2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Méthode setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la taille du paquet réseau actuelle utilisée pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], spécifié en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *PacketSize*  
  
 Un **int** valeur contenant la taille du paquet réseau.  
  
## <a name="remarks"></a>Notes  
 La plage acceptable de valeurs de cette propriété est [-1 | 0 | 512..32767]. Si cette propriété est définie sur une valeur située en dehors des limites acceptables, une exception se produit.  
  
 L'application peut souhaiter définir la propriété packetSize pendant la connexion à l'aide du chiffrement SSL (Secure Sockets Layer). Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] négocie la taille du paquet avec le serveur. Si la propriété encrypt a la valeur «**true**» et la taille négociée du paquet est supérieure à la taille d’enregistrement du fournisseur de sécurité par défaut la Machine virtuelle Java (JVM) de SSL, le pilote génère une erreur et l’arrête.  
  
 De plus, l'application peut souhaiter définir la propriété packetSize sans demander de chiffrement SSL. Dans ce cas, si le serveur requiert que le client prenne en charge le chiffrement SSL, le pilote vérifie la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java. Si la propriété packetSize est supérieure à la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java, le pilote génère une erreur et met fin à la connexion.  
  
 Pour plus d’informations sur l’utilisation de SSL, consultez [le chiffrement SSL à l’aide de](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
