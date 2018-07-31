---
title: Utilisation du chiffrement sans Validation | Microsoft Docs
description: Utilisation du chiffrement sans validation
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], encryption
- cryptography [OLE DB Driver for SQL Server]
- MSOLEDBSQL, encryption
- encryption [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, encryption
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: bdb35bf030598f1a206a6d2529095f23068cc841
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108891"
---
# <a name="using-encryption-without-validation"></a>Utilisation du chiffrement sans validation
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chiffre toujours les paquets réseau associés à l’ouverture de session. Si aucun certificat n'a été fourni sur le serveur à son démarrage, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] génère un certificat auto-signé qui est utilisé pour chiffrer les paquets d’ouverture de session.  

Les certificats auto-signés ne garantissent pas la sécurité. Le protocole de transfert chiffré est basé sur NT LAN Manager (NTLM). Il est recommandé de mettre en service un certificat vérifiable sur SQL Server pour une connectivité sécurisée. Sécurité TLS (Transport Layer) est possible sécurisé uniquement avec la validation du certificat.

Les applications peuvent également demander le chiffrement de tout le trafic réseau en utilisant des mots clés de chaîne de connexion ou des propriétés de connexion. Ces mots clés sont « Encrypt » pour OLE DB en cas d’utilisation d’une chaîne de fournisseur avec **IDbInitialize::Initialize** ou « Use Encryption for Data » pour ADO et OLE DB en cas d’utilisation d’une chaîne d’initialisation avec **IDataInitialize**. Cela peut également être configuré par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide du Gestionnaire de Configuration le **forcer le chiffrement du protocole** option et la configuration par le client pour demander des connexions chiffrées. Par défaut, le chiffrement de tout le trafic réseau pour une connexion requiert la fourniture d'un certificat sur le serveur. En définissant votre client faire confiance au certificat sur le serveur, vous pouvez devenir vulnérable aux attaques par man-in-the-middle. Si vous déployez un certificat vérifiable sur le serveur, veillez à modifier les paramètres du client sur le certificat de confiance sur FALSE.

Pour plus d’informations sur les mots clés de chaîne de connexion, consultez [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md ).  
  
 Pour activer le chiffrement à utiliser quand aucun certificat n’a été provisionné sur le serveur, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut être utilisé pour définir les options **Forcer le chiffrement du protocole** et **Faire confiance au certificat de serveur**. Dans ce cas, le chiffrement utilise un certificat de serveur auto-signé sans validation si aucun certificat vérifiable n'a été fourni sur le serveur.  
  
 Les applications peuvent également utiliser le mot clé « TrustServerCertificat » ou son attribut de connexion associé pour garantir que le chiffrement est réalisé. Les paramètres de l'application ne réduisent jamais le niveau de sécurité défini par le Gestionnaire de configuration du client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], mais peuvent le renforcer. Par exemple, si l’option **Forcer le chiffrement du protocole** n’est pas définie pour le client, une application peut demander elle-même le chiffrement. Pour garantir le chiffrement même si aucun certificat de serveur n'a été fourni, une application peut demander le chiffrement et « TrustServerCertificate ». Toutefois, si« TrustServerCertificate » n'est pas activé dans la configuration client, un certificat de serveur fourni est toujours requis. Le tableau ci-dessous décrit l'ensembles des scénarios :  
  
|Paramètre client Forcer le chiffrement du protocole|Paramètre client Faire confiance au certificat de serveur|Chaîne de connexion/attribut de connexion Encrypt/Use Encryption for Data|Chaîne de connexion/attribut de connexion Trust Server Certificate|Résultats|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|non|Néant|Non (par défaut)|Ignoré|Aucun chiffrement ne se produit.|  
|non|Néant|Oui|Non (par défaut)|Le chiffrement se produit uniquement s'il existe un certificat de serveur vérifiable ; sinon, la tentative de connexion échoue.|  
|non|Néant|Oui|Oui|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
|Oui|non|Ignoré|Ignoré|Le chiffrement se produit uniquement s'il existe un certificat de serveur vérifiable ; sinon, la tentative de connexion échoue.|  
|Oui|Oui|Non (par défaut)|Ignoré|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
|Oui|Oui|Oui|Non (par défaut)|Le chiffrement se produit uniquement s'il existe un certificat de serveur vérifiable ; sinon, la tentative de connexion échoue.|  
|Oui|Oui|Oui|Oui|Le chiffrement se produit toujours, mais peut utiliser un certificat de serveur auto-signé.|  
||||||

> [!CAUTION]
> Le tableau précédent fournit uniquement un guide sur le comportement du système sous différentes configurations. Pour une connectivité sécurisée, vérifiez que le client et serveur exiger le chiffrement. Vérifiez également que le serveur dispose d’un certificat vérifiable et que le **TrustServerCertificate** sur le client est défini sur FALSE.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server 
 OLE DB Driver pour SQL Server prend en charge le chiffrement sans validation par le biais de l’ajout de la propriété d’initialisation de la source de données SSPROP_INIT_TRUST_SERVER_CERTIFICATE, implémentée dans le jeu de propriétés DBPROPSET_SQLSERVERDBINIT. De plus, un nouveau mot clé de chaîne de connexion, « TrustServerCertificate» , a été ajouté. Il accepte les valeurs « oui » ou « non », « non » étant la valeur par défaut. Lors de l'utilisation de composants du service, il accepte les valeurs true ou false ; false étant la valeur par défaut.  
  
 Pour plus d’informations sur les améliorations apportées au jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [propriétés d’initialisation et d’autorisation](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  

  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
