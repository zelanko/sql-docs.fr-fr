---
title: "Inscrire le référentiel de la disponibilité générale de SQL Server sur Linux | Documents Microsoft"
description: "Modifier les référentiels à partir du référentiel SQL Server 2017 d’aperçu dans le référentiel de disponibilité générale sur Linux (disponibilité générale est parfois également appelé RTM)."
author: annashres
ms.author: anshrest
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: f74c74bddf8337bf4555ce4ecdf0b6e2c869e44f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="change-repositories-from-the-preview-repository-to-the-ga-repository"></a>Modification des référentiels à partir du référentiel d’aperçu dans le référentiel GA

Lorsque vous mettez à niveau SQL Server 2017 CTP 2.1, RC1 ou RC2 vers la version disponibilité générale (GA), vous devez basculer les référentiels. Les sections suivantes expliquent de référentiels et comment effectuer la modification avant la mise à niveau.

## <a name="repository-choices"></a>Choix de référentiel

Il est important de noter qu’il existe deux principaux types de référentiels pour chaque point de distribution :

  > [!IMPORTANT]
  > N’importe quelle version avant CTP 2.1 doit être mis à niveau au moins 2.1 avant la mise à niveau de disponibilité générale.

- **Les mises à jour cumulative (CU)**: référentiel de la mise à jour Cumulative (CU) contient des packages pour la version de SQL Server de base et tous les correctifs de bogues ou améliorations apportées depuis cette version. Mises à jour cumulatives sont spécifiques à une version release, telles que SQL Server 2017. Ils sont publiés sur une cadence régulière.

- **GDR**: référentiel du GDR contient des packages pour la base version de SQL Server et uniquement les correctifs critiques et les mises à jour de sécurité depuis cette version. Ces mises à jour sont également ajoutés à la prochaine version CU.

Chaque version de CU et correctif logiciel grand public contient le package SQL Server complète et toutes les mises à jour précédentes pour ce référentiel. Mise à jour à partir d’une version GDR vers une version CU prend en charge la modification de votre référentiel configuré pour SQL Server. Vous pouvez également [rétrograder](sql-server-linux-setup.md#rollback) à n’importe quelle version dans votre version principale (ex : 2017).

> [!NOTE]
> Vous pouvez mettre à jour à partir d’une version GDR CU libérer à tout moment en modifiant les référentiels. Mise à jour à partir d’une CU version à une version de correctif logiciel grand public n’est pas pris en charge. 

## <a name="change-to-a-ga-repository"></a>Remplacez par un référentiel GA

Pour modifier à partir du référentiel de l’aperçu dans un référentiel de code source (CU ou GDR), procédez comme suit :

1. Supprimer le référentiel d’aperçu précédemment configurés.

   | Plateforme | Commande de suppression de référentiel |
   |-----|-----|
   | RHEL | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | Ubuntu | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |

1. Pour **Ubuntu uniquement**, importation des clés publiques de référentiel GPG.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Configurez le nouveau référentiel.

   | Plateforme | Référentiel | Command |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [Installer](sql-server-linux-setup.md#platforms) ou [mettre à jour](sql-server-linux-setup.md#upgrade) SQL Server à l’aide de l’espace de stockage GA.

   > [!IMPORTANT]
   > À ce stade, si vous choisissez d’effectuer une installation complète à l’aide de la [didacticiels de démarrage rapide](#platforms), souvenez-vous que vous venez de configurer le référentiel cible. Ne répétez pas cette étape dans les didacticiels. Cela est particulièrement vrai si vous configurez le référentiel GDR, étant donné que les didacticiels de démarrage rapide utilisent le référentiel CU.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’installation de SQL Server 2017 sur Linux, consultez [aide à l’Installation de SQL Server sur Linux](sql-server-linux-setup.md).
