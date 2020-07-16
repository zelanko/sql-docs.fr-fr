---
title: Régénérer des procédures personnalisées pour les modifications de schéma (articles transactionnels)
description: Regénérez des procédures stockées transactionnelles personnalisées afin de refléter des modifications de schéma pour la réplication transactionnelle.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9616c11a1d17f2634ef0b525dd23ac8b31203ddc
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159387"
---
# <a name="transactional-articles---regenerate-to-reflect-schema-changes"></a>Articles transactionnels - Regénérer pour refléter les modifications de schéma
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Par défaut, la réplication transactionnelle effectue toutes les modifications de données sur l'Abonné via des procédures stockées qui sont générées par des procédures internes pour chaque article de table de la publication. Les trois procédures (une pour les insertions, une pour les mises à jour et une pour les suppressions) sont copiées vers l'Abonné et s'exécutent quand une insertion, une mise à jour ou une suppression est répliquée vers l'Abonné. Quand une modification de schéma est apportée à une table sur un serveur de publication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , la réplication régénère automatiquement ces procédures en appelant le même ensemble de procédures de script internes, de façon à ce que les nouvelles procédures correspondent au nouveau schéma (la réplication de modifications de schéma n'est pas prise en charge pour les serveurs de publication Oracle).  
  
 Il est également possible de spécifier des procédures personnalisées pour remplacer une ou plusieurs des procédures par défaut. Les procédures personnalisées doivent être modifiées si la modification de schéma affecte la procédure. Par exemple, si une procédure référence une colonne qui est supprimée dans une modification de schéma, les références à la colonne doivent être supprimées de la procédure. Il y a deux façons pour la réplication de propager une nouvelle procédure personnalisée vers les Abonnés :  
  
-   La première option consiste à utiliser une procédure de script personnalisée pour remplacer les procédures par défaut utilisées par la réplication :  
  
    1.  Quand vous exécutez [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), assurez-vous que le bit 0x02 de `@schema_option` a la valeur **true**.  
  
    2.  Exécutez [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) et spécifiez la valeur 'insert', 'update' ou 'delete' pour le paramètre `@type`, et le nom de la procédure de script personnalisée pour le paramètre `@value`.  
  
     La prochaine fois qu'une modification de schéma est effectuée, la réplication appelle cette procédure stockée pour générer le script de la définition de la nouvelle procédure stockée personnalisée définie par l'utilisateur, puis propage la procédure à chaque Abonné.  
  
-   La deuxième option consiste à utiliser un script qui contient une nouvelle définition de procédure personnalisée :  
  
    1.  Quand vous exécutez [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), affectez au bit 0x02 de `@schema_option` la valeur **false**, de façon à ce que la réplication ne génère pas automatiquement des procédures personnalisées sur l’Abonné.  
  
    2.  Avant chaque modification de schéma, créez un nouveau fichier de script et inscrivez le script avec la réplication en exécutant [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Spécifiez la valeur 'custom_script' pour le paramètre `@type`, et le chemin du script sur le serveur de publication pour le paramètre `@value`.  
  
     La prochaine fois qu'une modification de schéma pertinente est effectuée, ce script s'exécutera sur chaque Abonné au sein de la même transaction que la commande DDL. Quand la modification de schéma est effectuée, le script est désinscrit. Vous devez réinscrire le script pour qu'il soit exécuté après une modification de schéma ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier le mode de propagation des modifications des articles transactionnels](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
