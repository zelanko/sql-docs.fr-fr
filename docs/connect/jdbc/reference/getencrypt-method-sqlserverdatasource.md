---
description: Méthode getEncrypt (SQLServerDataSource)
title: Méthode getEncrypt (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09beeea5d623e50d5fcdbf562151631cbc67124d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436131"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Méthode getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la propriété encrypt est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le chiffrement est activé. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété encrypt a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] vérifie que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le chiffrement TLS pour toutes les données envoyées entre le client et le serveur, si un certificat est installé sur le serveur.  
  
 Si la propriété encrypt n’est pas spécifiée ou si elle a la valeur **false**, le pilote n’impose pas à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la prise en charge du chiffrement TLS. Si l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n’est pas configurée pour imposer le chiffrement TLS, une connexion est établie sans aucun chiffrement. Si l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est configurée pour forcer le chiffrement TLS, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] active automatiquement le chiffrement TLS lors de l’exécution sur une machine virtuelle Java (JVM) correctement configurée ; sinon, la connexion est interrompue et le pilote génère une erreur. Si la propriété de chiffrement n’est pas définie, la méthode [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) retourne la valeur par défaut **false**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
