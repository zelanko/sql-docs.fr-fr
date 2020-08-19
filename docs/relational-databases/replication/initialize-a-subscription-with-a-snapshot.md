---
description: Initialiser un abonnement avec un instantané pour une nouvelle publication
title: Initialiser un abonnement avec un instantané
ms.custom: ''
ms.date: 03/23/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 526be3921fa6b842415f0fbd2c78e2fd66981253
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475537"
---
# <a name="initialize-a-subscription-with-a-snapshot-for-a-new-publication"></a>Initialiser un abonnement avec un instantané pour une nouvelle publication

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

Cet article décrit les processus qui se produisent quand une publication de réplication est initialisée. Un instantané initial est appliqué aux Abonnés.

## <a name="snapshot-for-a-new-publication"></a>Instantané pour une nouvelle publication

Par défaut, un instantané est capturé après la création d’une publication.
L’instantané est copié dans le dossier d’instantanés. Ce comportement par défaut se produit pour les publications de fusion créées à l’aide de l’Assistant Nouvelle publication.

### <a name="snapshot-is-applied-to-subscriber"></a>L’instantané est appliqué à l’Abonné

Le nouvel instantané est appliqué à l’Abonné par un agent. L’application se produit lors de la synchronisation initiale de l’abonnement. L’agent qui effectue l’application dépend du type de publication :

- Pour les publications _transactionnelles_ et d’_instantané_ :
  - L'Agent de distribution.

- Pour les publications de _fusion_ :
  - L'Agent de fusion.

### <a name="type-of-publication"></a>Type de publication

Le tableau suivant affiche le contenu de l’instantané, pour chaque type de publication.

&nbsp;

| Type de publication cible de l’instantané | Contenu de l’instantané |
| :---------------------------------------- | :----------------------- |
| <ul> <li>Publication d'instantané</li> <li>Publication transactionnelle</li> <li>Publication de fusion n’utilisant pas de filtres paramétrés</li> </ul> | <ul> <li>schéma</li> <li>Données, dans les fichiers pour le programme de copie en bloc (BCP)</li> <li>Contraintes</li> <li>Propriétés étendues</li> <li>Index</li> <li>Déclencheurs</li> <li>Tables système nécessaires à la réplication</li> </ul> <br/>Consultez [Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md). |
| <ul> <li>Publication de fusion utilisant des filtres paramétrés</li> </ul> | <ul> <li>Instantané de schéma (scripts de réplication, objets publiés, mais pas de données)</li> <li>Données qui appartiennent à la partition de l’abonnement</li> </ul> <br/>Consultez [Instantanés des publications de fusion avec des filtres paramétrés](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). |
| | |

#### <a name="two-part-process-with-merge-publication-that-uses-parameterized-filters"></a>Processus en deux parties avec publication de fusion qui utilise des filtres paramétrés

Pour une publication de fusion utilisant des filtres paramétrés, l’instantané est créé à l’aide du processus en deux parties suivant :

1. Un instantané de schéma est créé, qui contient les éléments suivants :
   - Scripts de réplication.
   - Schéma des objets publiés.
   - _(Mais pas de données.)_

2. Chaque abonnement est ensuite initialisé avec un instantané. L’instantané comprend les éléments suivants :
   - Scripts et schéma, copiés à partir de l’instantané de schéma.
   - Données qui appartiennent à la partition de l’abonnement.

## <a name="type-of-replication"></a>Type de réplication

Les types de fichiers contenus dans l’instantané dépendent du type de réplication et des articles de votre publication.

&nbsp;

| Type de réplication | Fichiers d'instantanés courants |
| :------------------ | :-------------------- |
| Réplication d’instantané ou<br/>Réplication transactionnelle | &bullet; Schéma (.sch) <br/>&bullet; Données (.bcp) <br/>&bullet; Contraintes et index (.dri) <br/>&bullet; Fichiers d’instantanés compressés (.cab) <br/>&bullet; Déclencheurs (.tag), uniquement pour mettre à jour un Abonné <br/><br/>&bullet; Contraintes (.idx). |
| Réplication de fusion                                      | &bullet; Schéma (.sch) <br/>&bullet; Données (.bcp) <br/>&bullet; Contraintes et index (.dri) <br/>&bullet; Fichiers d’instantanés compressés (.cab) <br/>&bullet; Déclencheurs (.trg) <br/><br/>&bullet; Données de table système (.sys) <br/>&bullet; Tables de conflits (.cft). |
| | |

### <a name="snapshot-folder"></a>Dossier d'instantanés

Les fichiers sont transférés en étant copiés dans le _dossier d’instantanés_ par défaut ou dans le _dossier de remplacement_ pour les instantanés.

Le dossier d’instantanés est spécifié lors de la configuration du serveur de distribution. Le dossier de remplacement est spécifié lors de la création de la publication.

### <a name="resume-transfer-after-interruption"></a>Reprendre le transfert après une interruption

Le transfert de fichiers vers un dossier d’instantanés reprend automatiquement si le transfert est interrompu par une connexion non fiable.

Pour plus d’efficacité, la reprise ne renvoie pas les fichiers qui ont déjà été complètement transférés avant l’interruption.

## <a name="snapshot-options"></a>Options d'instantané

Plusieurs options sont disponibles lors de l’initialisation d’un abonnement avec un instantané. Vous pouvez :

- Spécifier un emplacement de dossier d'instantanés de remplacement à la place, ou en plus de l'emplacement de dossier d'instantanés par défaut. Pour plus d’informations, consultez [Modifier les options des instantanés](../../relational-databases/replication/snapshot-options.md).

- Compresser les instantanés pour un stockage sur support amovible ou pour un transfert sur un réseau lent. Pour plus d’informations, consultez [Compressed Snapshots](../../relational-databases/replication/snapshot-options.md#compressed-snapshots).

- Exécuter des scripts Transact-SQL avant ou après l'application de l'instantané. Pour plus d’informations, consultez [Exécuter des scripts avant et après l’application de l’instantané](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).

- Transférer des fichiers d'instantanés via le protocole FTP. Pour plus d’informations, consultez [Transférer des instantanés via FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).

## <a name="see-also"></a>Voir aussi

[Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md)

[Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md)
