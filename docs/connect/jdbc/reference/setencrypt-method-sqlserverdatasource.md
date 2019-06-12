---
title: getXopenStates, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setEncrypt Method (SQLServerDataSource)
apilocation:
- setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8bb95e1eb547037d7ecf1855f71fa519102cf621
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773493"
---
# <a name="setencrypt-method-sqlserverdatasource"></a>Méthode setEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si la propriété encrypt est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *encrypt*  
  
 **true** si le chiffrement Secure Sockets Layer (SSL) est activé entre le client et le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété encrypt est définie sur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] vérifie que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le chiffrement SSL pour toutes les données envoyées entre le client et le serveur, si un certificat est installé sur le serveur. La valeur par défaut est **false**.  
  
 Le pilote JDBC détecte la machine virtuelle Java (JVM) sur laquelle il est exécuté lors de la tentative d'établissement d'une négociation SSL.  
  
 Si la propriété de chiffrement a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] utilise le fournisseur de sécurité JSSE par défaut de la machine virtuelle Java pour négocier le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le fournisseur de sécurité par défaut peut ne pas prendre en charge toutes les fonctionnalités requises pour négocier le chiffrement SSL avec succès. Par exemple, le fournisseur de sécurité par défaut peut ne pas prendre en charge la taille de la clé publique RSA utilisée dans le certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Dans ce cas, le fournisseur de sécurité par défaut peut générer une erreur qui forcera le pilote JDBC à mettre fin à la connexion. Pour résoudre ce problème, effectuez l'une des opérations suivantes :  
  
-   Configurer l’ordinateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec un certificat de serveur qui a une plus petite clé publique RSA  
  
-   Configurer la machine virtuelle Java de façon à utiliser un autre fournisseur de sécurité JSSE dans le fichier de propriétés de sécurité « \<java-home>/lib/security/java.security »  
  
-   Utiliser une autre machine virtuelle Java  
  
 Si la propriété encrypt n’est pas spécifiée ou si elle est définie sur **false**, le pilote n’impose pas à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la prise en charge du chiffrement SSL. Si l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n’est pas configurée pour imposer le chiffrement SSL, une connexion est établie sans aucun chiffrement. Si l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est configurée pour imposer le chiffrement SSL, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] active automatiquement le chiffrement SSL lors de l’exécution sur une machine virtuelle Java (JVM) correctement configurée ; sinon, la connexion est interrompue et le pilote génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
