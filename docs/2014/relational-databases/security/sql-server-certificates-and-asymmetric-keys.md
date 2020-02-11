---
title: Certificats et clés asymétriques SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server], certificates and asymmetric keys
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: ddb7e84f69f501a7857b0d55b1b8a14d11a85694
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75244514"
---
# <a name="sql-server-certificates-and-asymmetric-keys"></a>Certificats et clés asymétriques SQL Server
  Le chiffrement à clé publique (PKI) est une forme de confidentialité des messages dans laquelle un utilisateur crée une clé *publique* et une clé *privée* . La clé privée est gardée secrète, alors que la clé publique peut être distribuée aux autres. Bien que les clés soient liées mathématiquement, la clé privée ne peut pas être dérivée facilement de la clé publique. La clé publique est utilisée pour chiffrer les données et la clé privée pour les déchiffrer. Un message chiffré à l'aide de la clé publique peut être déchiffré uniquement à l'aide de la clé privée appropriée. Comme il existe deux clés différentes, ces clés sont *asymétriques*.  
  
 Les certificats et les clés asymétriques sont deux façons d'utiliser un chiffrement asymétrique. Les certificats sont souvent utilisés comme conteneurs pour les clés asymétriques car ils peuvent contenir plus d'informations, telles que les dates d'expiration et les émetteurs. Il n'y a aucune différence entre les deux mécanismes en ce qui concerne l'algorithme de chiffrement et aucune différence de puissance pour une même longueur de clé. En général, vous utilisez un certificat pour chiffrer d'autres types de clés de chiffrement dans une base de données ou pour signer des modules de code.  
  
 Les certificats et les clés asymétriques permettent de déchiffrer des données chiffrées par l'autre. En général, vous utilisez un chiffrement asymétrique pour chiffrer une clé symétrique afin de la stocker dans une base de données.  
  
 Une clé publique n'a pas de format particulier à la différence d'un certificat, et vous ne pouvez pas l'exporter dans un fichier.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des fonctionnalités qui vous permettent de créer et gérer des certificats et des clés en vue de les utiliser avec le serveur et la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne permet pas de créer ni de gérer des certificats et des clés avec d'autres applications ou dans le système d'exploitation.  
  
## <a name="certificates"></a>Certificats  
 Un certificat est un objet de sécurité signé numériquement qui contient une clé publique (voire éventuellement une clé privée) pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez utiliser des certificats générés de manière externe ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut générer les certificats.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les certificats sont conformes à la norme IETF X.509v3 relative aux certificats.  
  
 Les certificats sont utiles en raison de l'option permettant d'exporter et d'importer des clés dans des fichiers de certificat X.509. La syntaxe permettant de créer des certificats prend en compte des options de création de certificats, telles qu'une date d'expiration.  
  
### <a name="using-a-certificate-in-sql-server"></a>Utilisation d'un certificat dans SQL Server  
 Les certificats peuvent être utilisés pour mieux sécuriser des connexions, dans la mise en miroir de bases de données, pour signer des packages et d'autres objets, ou pour chiffrer des données ou des connexions. Le tableau ci-dessous répertorie des ressources supplémentaires pour les certificats dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)|Explique la commande permettant de créer des certificats.|  
|[Identifier la source de packages à l'aide de signatures numériques](../../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)|Fournit des informations sur la façon d'utiliser des certificats pour signer des packages logiciels.|  
|[Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|Fournit des informations sur la façon d'utiliser les certificats avec la mise en miroir de bases de données.|  
  
## <a name="asymmetric-keys"></a>Clés asymétriques  
 Les clés asymétriques permettent de sécuriser des clés symétriques. Elles peuvent également être utilisées pour un chiffrement de données limité et pour signer numériquement des objets de base de données. Une clé asymétrique se compose d'une clé privée et d'une clé publique correspondante. Pour plus d’informations sur les clés asymétriques, consultez [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql).  
  
 Les clés asymétriques peuvent être importées à partir de fichiers de clé de nom fort, mais elles ne peuvent pas être exportées. Elles n'ont pas non plus d'options d'expiration. Les clés asymétriques ne permettent pas de chiffrer des connexions.  
  
### <a name="using-an-asymmetric-key-in-sql-server"></a>Utilisation d'une clé asymétrique dans SQL Server  
 Les clés asymétriques permettent de mieux sécuriser des données ou de signer du texte en clair. Le tableau ci-dessous répertorie des ressources supplémentaires pour les clés asymétriques dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|Explique la commande permettant de créer des clés asymétriques.|  
|[SIGNBYASYMKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/signbyasymkey-transact-sql)|Affiche les options disponibles pour signer des objets.|  
  
## <a name="tools"></a>Outils  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] fournit des outils et des utilitaires qui généreront des certificats et des fichiers de clé de nom fort. Ces outils permettent une flexibilité accrue dans le processus de génération de clé par rapport à la syntaxe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez utiliser ces outils pour créer des clés RSA avec des longueurs de clé plus complexes, puis les importer dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le tableau ci-dessous indique où ces outils se trouvent.  
  
|||  
|-|-|  
|Outil|Objectif|  
|[makecert](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|Crée des certificats.|  
|[sn](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|Crée des noms forts pour les clés symétriques.|  
  
## <a name="related-tasks"></a>Tâches associées  
 [Choisir un algorithme de chiffrement](encryption/choose-an-encryption-algorithm.md)  
  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)   
 [Chiffrement transparent des données &#40;TDE&#41;](encryption/transparent-data-encryption.md)  
  
