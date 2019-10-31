---
title: Nouveautés de SQL Server 2019 sur Linux
description: Cet article présente les nouveautés de SQL Server 2019 sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5183efa51afd89ad82d0cdcb6448996429b81d28
ms.sourcegitcommit: bb56808dd81890df4f45636b600aaf3269c374f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890556"
---
# <a name="whats-new-for-sql-server-2019-on-linux"></a>Nouveautés de SQL Server 2019 sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit les principaux services et fonctionnalités disponibles pour SQL Server 2019 s’exécutant sur Linux. Pour connaitre les téléchargements de packages et les problèmes connus, consultez les [Notes de publication](sql-server-linux-release-notes-2019.md?view=sql-server-linux-ver15).

## <a name="updates"></a>Mises à jour

Les mises à jour ont été effectuées dans SQL Server 2019 sur Linux :

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Prise en charge de la réplication |[Réplication SQL Server sur Linux](sql-server-linux-replication.md)
|Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator) |[Comment configurer MSDTC sur Linux](sql-server-linux-configure-msdtc.md) |
|Prise en charge d’OpenLDAP pour les fournisseurs AD tiers |[Tutoriel : Utiliser l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md) |
|Machine learning sur Linux |[Configurer le Machine Learning sur Linux](sql-server-linux-setup-machine-learning.md) |
|Améliorations `tempdb` | Par défaut, une nouvelle installation de SQL Server sur Linux crée plusieurs fichiers de données `tempdb` en fonction du nombre de cœurs logiques (avec jusqu’à 8 fichiers de données). Cela ne s’applique pas aux mises à niveau de versions mineures ou majeures sur place. Chaque fichier `tempdb` fait 8 Mo avec une croissance automatique de 64 Mo. Ce comportement est similaire à l’installation de SQL Server par défaut sur Windows. |
| PolyBase sur Linux | [Installer PolyBase](../relational-databases/polybase/polybase-linux-setup.md) sur Linux pour les connecteurs non-Hadoop.<br/><br/>[Mappage de type PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Prise en charge de la capture des changements de données (CDC) | La capture des changements de données (CDC) est désormais prise en charge sur Linux pour SQL Server 2019. |
| Registre de conteneurs Microsoft | Le [registre de conteneurs Microsoft](https://www.ntweekly.com/2019/09/23/microsoft-container-registry-to-replace-docker-hub-for-new-images/) remplace désormais Docker Hub pour les nouvelles images conteneur Microsoft officielles, notamment [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |
| Conteneurs non racines | [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit la possibilité de créer des conteneurs plus sûrs en démarrant le processus [!INCLUDE[sql-server](../includes/ssnoversion-md.md)] en tant qu’utilisateur non racine par défaut. Pour plus d’informations, consultez [Générer et exécuter des conteneurs SQL Server en tant qu’utilisateur non racine](sql-server-linux-configure-docker.md#buildnonrootcontainer). |

## <a name="next-steps"></a>Étapes suivantes

Pour installer SQL Server sur Linux, utilisez l’un des didacticiels suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md?view=sql-server-linux-ver15)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md?view=sql-server-linux-ver15)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md?view=sql-server-linux-ver15)
- [Exécuter sur Docker](quickstart-install-connect-docker.md?view=sql-server-linux-ver15)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Pour obtenir des réponses aux questions fréquemment posées, consultez la [FAQ de SQL Server sur Linux](sql-server-linux-faq.md). Pour voir d’autres améliorations introduites dans SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
