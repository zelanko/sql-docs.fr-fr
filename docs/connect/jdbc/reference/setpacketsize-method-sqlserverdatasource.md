---
title: Méthode setPacketSize (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8e3affcbb2181cf8979196c65a0bcd81e58c541e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973284"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Méthode setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la taille de paquet réseau actuelle utilisée pour communiquer avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], spécifiée en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *packetSize*  
  
 Valeur **int** contenant la taille de paquet réseau.  
  
## <a name="remarks"></a>Notes  
 La plage acceptable de valeurs de cette propriété est [-1 | 0 | 512..32767]. Si cette propriété est définie sur une valeur située en dehors des limites acceptables, une exception se produit.  
  
 L'application peut souhaiter définir la propriété packetSize pendant la connexion à l'aide du chiffrement SSL (Secure Sockets Layer). Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] négocie la taille de paquet avec le serveur. Si la propriété encrypt a la valeur « **true** » et que la taille négociée du paquet est supérieure à la taille de l’enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java (JVM), le pilote génère une erreur et met fin à la connexion.  
  
 De plus, l'application peut souhaiter définir la propriété packetSize sans demander de chiffrement SSL. Dans ce cas, si le serveur requiert que le client prenne en charge le chiffrement SSL, le pilote vérifie la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java. Si la propriété packetSize est supérieure à la taille d'enregistrement SSL du fournisseur de sécurité par défaut de la machine virtuelle Java, le pilote génère une erreur et met fin à la connexion.  
  
 Pour plus d’informations sur l’utilisation du protocole SSL, consultez [Utilisation du chiffrement SSL](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
