---
title: Chiffrement SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: f5838d497808e9a251522536a00d590403674eda
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053769"
---
# <a name="sql-server-encryption"></a>Chiffrement SQL Server
  Le chiffrement est un processus visant à rendre des données inintelligibles à l'aide d'une clé ou d'un mot de passe. Les données sont alors inutiles en l'absence du mot de passe ou de la clé de déchiffrement correspondante. Le chiffrement ne résout pas les problèmes de contrôle d'accès. Toutefois, il améliore la sécurité en limitant les pertes de données même si les contrôles d'accès sont contournés. Par exemple, si l'ordinateur hôte de la base de données est mal configuré et qu'un pirate parvient à se procurer des données sensibles, les données subtilisées seront vraisemblablement inexploitables si elles sont chiffrées.  
  
 Vous pouvez utiliser le chiffrement dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les connexions, les données et les procédures stockées. Le tableau ci-dessous contient davantage d'informations sur le chiffrement dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Bien que le chiffrement soit un outil précieux qui aide à garantir la sécurité, il ne doit pas être envisagé pour toutes les données et connexions. Lorsque vous décidez de mettre en œuvre ou non le chiffrement, tenez compte de la manière dont les utilisateurs accèderont aux données. Si les utilisateurs accèdent aux données via un réseau public, le chiffrement des données peut être requis pour augmenter la sécurité. Toutefois, si tous les accès impliquent une configuration intranet sécurisée, le chiffrement peut s'avérer superflu. Toute utilisation du chiffrement doit également inclure une stratégie de maintenance pour les mots de passe, les clés et les certificats.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Hiérarchie de chiffrement](encryption-hierarchy.md)  
 Informations sur la hiérarchie de chiffrement dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Choisir un algorithme de chiffrement](choose-an-encryption-algorithm.md)  
 Informations sur la manière de sélectionner un algorithme de chiffrement efficace.  
  
 [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md)  
 Informations générales sur la manière de chiffrer des données de façon transparente.  
  
 [SQL Server et clés de chiffrement de base de données &#40;moteur de base de données&#41;](sql-server-and-database-encryption-keys-database-engine.md)  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les clés de chiffrement incluent une combinaison d'une clé publique, d'une clé privée et d'une clé symétrique, dont le but est de protéger les données sensibles. Cette section explique comment implémenter et gérer des clés de chiffrement.  
  
## <a name="related-content"></a>Contenu associé  
 [Sécurisation de SQL Server](../securing-sql-server.md)  
 Vue d'ensemble du processus permettant de mieux sécuriser la plateforme [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et du travail avec des utilisateurs et des objets sécurisables.  
  
 [Fonctions de chiffrement &#40;Transact-SQL&#41;](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 Informations sur la manière d'implémenter des fonctions de chiffrement.  
  
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 Informations sur l'utilisation d'un mot de passe pour chiffrer des données.  
  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbykey-transact-sql)  
 Informations sur l'utilisation d'une clé symétrique pour chiffrer des données.  
  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 Informations sur l'utilisation d'une clé asymétrique pour chiffrer des données.  
  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbycert-transact-sql)  
 Informations sur l'utilisation d'un certificat pour chiffrer des données.  
  
## <a name="external-resources"></a>Ressources externes  
 [Microsoft TechNet : SQL Server TechCenter : SQL Server 2005 – Sécurité et protection](http://www.microsoft.com/technet/prodtechnol/sql/2005/library/security.mspx)  
 Informations à jour sur la sécurité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql)   
 [SQL Server et clés de chiffrement de base de données &#40;moteur de base de données&#41;](sql-server-and-database-encryption-keys-database-engine.md)   
 [Sauvegarder et restaurer les clés de chiffrement Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
