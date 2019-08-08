---
title: Pool de mémoires tampons hybride | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
ms.openlocfilehash: e4808c0895695eba562c25ea0ee412348dc148f5
ms.sourcegitcommit: 182ed49fa5a463147273b58ab99dc228413975b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68697554"
---
# <a name="hybrid-buffer-pool"></a>Pool de mémoires tampons hybride
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le pool de mémoires tampons hybride permet au moteur de base de données d’accéder directement aux pages de données dans les fichiers de base de données stockés sur des appareils à mémoire persistante (PMEM). Cette fonctionnalité est introduite dans [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)].

Dans un système traditionnel sans mémoire persistante, SQL Server met en cache les pages de données dans le pool de mémoires tampons. Avec le pool de mémoires tampons hybride, SQL Server passe outre l’exécution d’une copie de la page dans la partie DRAM du pool de mémoires tampons ; il accède à la page directement sur le fichier de base de données qui réside sur un appareil PMEM. L’accès en lecture aux fichiers de données sur les appareils PMEM pour le pool de mémoires tampons hybride s’effectue directement en suivant un pointeur vers les pages de données de l’appareil PMEM.  

Seules les pages nettoyées sont accessibles directement sur un appareil PMEM. Quand une page est marquée comme modifiée, elle est copiée dans le pool de mémoires tampons DRAM avant d’être écrite sur l’appareil PMEM et marquée comme étant nettoyée de nouveau. Cela se produit pendant les opérations de point de contrôle habituelles. Le mécanisme permettant de copier le fichier de l’appareil PMEM vers la mémoire DRAM est une opération d’E/S mappée en mémoire (MMIO) directe. On dit également que les fichiers de données dans SQL Server sont dans un *état d’éveil à la présence d’un environnement virtualisé*.


La fonctionnalité de pool de mémoires tampons hybride est disponible pour Windows et Linux. L’appareil PMEM doit être formaté avec un système de fichiers qui prend en charge DAX (DirectAccess). Les systèmes de fichiers XFS, EXT4 et NTFS prennent tous en charge DAX. SQL Server détecte automatiquement si les fichiers de données résident sur un appareil PMEM correctement mis en forme, et effectue le mappage en mémoire dans l’espace utilisateur. Ce mappage est effectué lors du démarrage, quand une nouvelle base de données est attachée, restaurée ou créée, ou quand la fonctionnalité de pool de mémoires tampons hybride est activée pour une base de données.

Pour plus d’informations sur la prise en charge de la mémoire persistante par Windows Server, consultez [Déployer une mémoire persistante sur Windows Server](/windows-server/storage/storage-spaces/deploy-pmem/).

Pour plus d’informations sur la configuration de SQL Server sur Linux pour des appareils PMEM, consultez [Déployer une mémoire persistante](../../linux/sql-server-linux-configure-pmem.md).

## <a name="enable-hybrid-buffer-pool"></a>Activer le pool de mémoires tampons hybride

[!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] introduit un langage dynamique de données (DDL) permettant de contrôler le pool de mémoires tampons hybride.

L’exemple suivant active le pool de mémoires tampons hybride pour une instance de SQL Server :

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = ON;
```

Par défaut, le pool de mémoires tampons hybride est désactivé dans l’étendue de l’instance. Notez que pour que la modification du paramètre prenne effet, l’instance de SQL Server doit être redémarrée. Un redémarrage est nécessaire afin de faciliter l’allocation de pages de hachage suffisantes pour prendre en compte la capacité PMEM totale sur le serveur.

L’exemple suivant active le pool de mémoires tampons hybride pour une base de données spécifique.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = ON;
```

Par défaut, le pool de mémoires tampons hybride est activé dans l’étendue de la base de données.

## <a name="disable-hybrid-buffer-pool"></a>Désactiver le pool de mémoires tampons hybride

L’exemple suivant désactive le pool de mémoires tampons hybride pour une instance de SQL Server :

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = OFF;
```

Par défaut, le pool de mémoires tampons hybride est désactivé dans l’étendue de l’instance. Notez que pour que la modification du paramètre prenne effet, l’instance de SQL Server doit être redémarrée. Un redémarrage est nécessaire afin d’empêcher une allocation trop élevée de pages de hachage, étant donné que la capacité PMEM sur le serveur n’a pas besoin d’être prise en compte.

L’exemple suivant désactive le pool de mémoires tampons hybride pour une base de données spécifique.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = OFF;
```

Par défaut, le pool de mémoires tampons hybride est activé dans l’étendue de la base de données.

## <a name="view-hybrid-buffer-pool-configuration"></a>Afficher la configuration du pool de mémoires tampons hybride

L’exemple suivant retourne l’état actuel de la configuration système du pool de mémoires tampons hybride pour une instance de SQL Server.

```sql
SELECT *
FROM sys.configurations
WHERE
    name = 'hybrid_buffer_pool';
```

L’exemple suivant retourne deux tables :

- La première indique l’état actuel de la configuration système du pool de mémoires tampons hybride pour une instance de SQL Server.
- La seconde liste les bases de données et le paramètre de niveau de base de données pour le pool de mémoires tampons hybride (`is_memory_optimized_enabled`).

```sql
SELECT * FROM sys.configurations WHERE name = 'hybrid_buffer_pool';

SELECT name, is_memory_optimized_enabled FROM sys.databases;
```

## <a name="best-practices-for-hybrid-buffer-pool"></a>Bonnes pratiques pour le pool de mémoires tampons hybride

Il n’est pas recommandé d’activer le pool de mémoires tampons hybride sur des instances avec moins de 16 Go de RAM.

Quand vous formatez votre appareil PMEM sur Windows, utilisez la plus grande taille d’unité d’allocation disponible pour NTFS (2 Mo dans Windows Server 2019) et vérifiez que l’appareil a été formaté pour DAX (Direct Access).

Les tailles de fichiers doivent être un multiple de 2 Mo (modulo 2 Mo doit être égal à zéro).

Si le paramètre d’étendue serveur pour le pool de mémoires tampons hybride est défini sur désactivé, ce dernier n’est utilisé par aucune base de données utilisateur.

Si le paramètre d’étendue serveur pour la mémoire tampon hybride est activé, vous pouvez désactiver l’utilisation du pool de mémoires tampons hybride pour des bases de données utilisateur individuelles en suivant les étapes permettant de désactiver le pool de mémoires tampons hybride au niveau de la base de données pour ces bases de données utilisateur.
