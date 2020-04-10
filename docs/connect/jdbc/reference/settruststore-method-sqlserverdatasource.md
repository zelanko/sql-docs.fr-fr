---
title: Méthode setTrustStore (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3d229e9e9c4758f43a090c1481d751560d072da
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901915"
---
# <a name="settruststore-method-sqlserverdatasource"></a>Méthode setTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le chemin d'accès (y compris le nom de fichier) au fichier trustStore de certificat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *trustStore*  
  
 Valeur **String** qui contient le chemin (notamment le nom de fichier) du fichier trustStore de certificat.  
  
## <a name="remarks"></a>Notes  
 Quand la propriété trustStore n’est pas spécifiée ou a la valeur Null, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] se fie aux règles de recherche de la fabrication du gestionnaire d’approbation pour déterminer le magasin de certificats à utiliser. Le TrustManagerFactory SunX509 par défaut essaie de rechercher les informations approuvées aux emplacements suivants dans cet ordre :  
  
-   1. Un fichier spécifié par la propriété système de machine virtuelle Java (JVM) « javax.net.ssl.trustStore ».  
  
-   2. Fichier « \<java-home>/lib/security/jssecacerts ».  
  
-   3. Fichier « \<java-home>/lib/security/cacerts ».  
  
 Pour plus d'informations, consultez la documentation d'interface SunX509 TrustManager sur le site Web de Sun Microsystems.  
  
 Si la propriété trustStore est définie avec une chaîne ou une valeur vide « », le pilote utilise cette valeur pour rechercher le fichier trustStore pour valider le certificat SSL du serveur.  
  
 La propriété trustStorePassword peut être spécifiée avec la propriété trustStore et sa valeur est utilisée pour ouvrir le fichier trustStore. Pour plus d’informations, consultez [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
