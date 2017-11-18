---
title: "Méthode setTrustStore (SQLServerDataSource) | Documents Microsoft"
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
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3e6de008468da81facf98c039457f9248ddddc49
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
  
 A **chaîne** qui contient le chemin d’accès (y compris le nom de fichier) au fichier trustStore de certificat.  
  
## <a name="remarks"></a>Notes  
 Si la propriété trustStore n’est pas spécifié ou défini comme null, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] s’appuient sur des règles pour déterminer le magasin de certificats à utiliser de recherche de la fabrique de gestionnaire de confiance. Le TrustManagerFactory SunX509 par défaut essaie de trouver les informations d’approbation dans les emplacements suivants dans cet ordre :  
  
-   1. Un fichier spécifié par la propriété système de machine virtuelle Java (JVM) « javax.net.ssl.trustStore ».  
  
-   2. «\<java-home >/lib/security/jssecacerts » fichier.  
  
-   3. «\<java-home >/lib/security/cacerts » fichier.  
  
 Pour plus d'informations, consultez la documentation d'interface SunX509 TrustManager sur le site Web de Sun Microsystems.  
  
 Si la propriété trustStore est définie avec une chaîne ou une valeur vide « », le pilote utilise cette valeur pour rechercher le fichier trustStore pour valider le certificat SSL du serveur.  
  
 La propriété trustStorePassword peut être spécifiée avec la propriété trustStore et sa valeur est utilisée pour ouvrir le fichier trustStore. Pour plus d’informations, consultez [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

