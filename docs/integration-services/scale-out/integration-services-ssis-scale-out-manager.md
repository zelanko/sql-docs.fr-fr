---
title: "SQL Server Integration Services avec le Gestionnaire de montée en puissance | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96748296acd1b2f5ba98558335fece9637eadb87
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-scale-out-manager"></a>Integration Services avec montée en puissance Manager

Échelle Out Manager est un outil de gestion qui vous permet de gérer votre topologie SSIS monter en charge complète à un seul endroit. Il supprime la charge de d’exploitation sur plusieurs ordinateurs et le traitement des commandes TSQL. 

Il existe deux façons pour déclencher le Gestionnaire de mise à l’échelle des.

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Ouvrir avec le Gestionnaire de montée en puissance à partir de SQL Server Management Studio
Ouvrez SQL Server Management Studio et connectez-vous à l’instance de SQL Server de montée en puissance Out principale.

Avec le bouton droit **SSISDB** dans l’Explorateur d’objets et sélectionnez **gérer les monter en charge...** . 
![Gérer la montée en puissance parallèle](media/manage-scale-out.PNG)

> [!NOTE]
> Il est recommandé d’exécuter SQL Server Management Studio en tant qu’administrateur en tant que certaines opérations de gestion à monter en charge tels que « l’ajout d’une montée en charge de travail » nécessite des privilèges d’administration.


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2. Ouvrir directement l’échelle Out Gestionnaire ISManager.exe en cours d’exécution

ISManager.exe localise sous %SystemDrive%\Program fichiers (x86) \Microsoft SQL Server\140\DTS\Binn\Management. Bouton droit sur **ISManager.exe** et sélectionnez « Exécuter en tant qu’administrateur ». 

Après son ouverture, vous devez entrer le nom de Sql Server de l’échelle des principales et s’y connecter avant de gérer votre monter en charge.

![Portail de connexion](media/portal-connect.PNG)

Échelle Out Manager offre diverses fonctionnalités, comme indiqué ci-dessous. 

## <a name="enable-scale-out"></a>Activer la montée en puissance parallèle
Après la connexion à SQL Server, si monter en charge n’est pas activé, vous pouvez cliquer sur le bouton « Activer » pour l’activer.

![Activer portail avec montée en puissance](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Afficher l’état de mise à l’échelle des principale
L’état de mise à l’échelle des principale s’affiche sur le **tableau de bord** page.

![Tableau de bord de portail](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Afficher l’état de mise à l’échelle des processus de travail
L’état de mise à l’échelle des processus de travail s’affiche sur le **travail Manager** page. Vous pouvez cliquer sur chaque processus de travail pour connaître l’état individuel.

![Gestionnaire de processus de travail de portail](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Ajouter la montée en charge de travail
Pour ajouter un montée en puissance des processus de travail, cliquez sur le bouton « + » en bas de la liste de montée en puissance des processus de travail. 

Entrez le nom de l’ordinateur de l’échelle des Worker vous souhaitez ajouter et cliquez sur « Valider ». Le Gestionnaire de mise à l’échelle les vérifie si l’utilisateur actuel a accès pour les magasins de certificats sur les ordinateurs de l’échelle des Master et de montée en puissance des processus de travail.

![Connecter des processus de travail](media/connect-worker.PNG)

Si la validation réussit, échelle Out Manager tente de lire votre travail de fichier de configuration et d’obtenir l’empreinte numérique du processus de travail. Pour plus d’informations, consultez [montée en puissance des processus de travail](integration-services-ssis-scale-out-worker.md). Si elle n’est pas en mesure de lire le processus de travail de fichier de configuration, il existe deux autres méthodes pour fournir le certificat du travail. 

Vous pouvez soit entrer l’empreinte numérique du certificat du travail directement 

![Certificat du travail 1](media/portal-cert1.PNG)

ou fournissez le fichier de certificat. 

![Certificat du travail 2](media/portal-cert2.PNG)

Une fois toutes les informations collectées, échelle Out Manager fournissent les actions à effectuer. Généralement, il inclut installation du certificat, mise à jour des fichiers de configuration travail et redémarrage du service de travail. 

![Ajout du portail confirmer 1](media/portal-add-confirm1.PNG)

Au cas où le certificat de travail n’est pas accessible, vous devez manuellement mettre à jour par vous-même et redémarrez le service de travail.

![Ajout du portail confirmer 2](media/portal-add-confirm2.PNG)

Cliquez sur la case à cocher Confirmer et commencer à ajouter la montée en puissance des processus de travail.

## <a name="delete-scale-out-worker"></a>Supprimer la montée en charge de travail
Pour supprimer un montée en puissance des processus de travail, sélectionnez le montée en puissance des processus de travail, puis cliquez sur le «- » situé en bas de la liste de montée en puissance des processus de travail.


## <a name="enabledisable-scale-out"></a>Activer/désactiver la montée en puissance parallèle
Pour activer ou désactiver un montée en puissance des processus de travail, sélectionnez le montée en puissance des processus de travail et cliquez sur le « Activer le processus de travail » ou « Désactiver le processus de travail ». L’état du travail sur l’échelle des Gestionnaire changent en conséquence si le processus de travail n’est pas hors connexion.

## <a name="edit-scale-out-worker-description"></a>Modifier la description de la montée en puissance des processus de travail
Pour modifier la description d’un montée en puissance des processus de travail, sélectionnez le montée en puissance des processus de travail, puis cliquez sur le bouton « Modifier ». Une fois que vous avez terminé, cliquez sur le bouton « Enregistrer ».

![Portail de travail de sauvegarde](media/portal-save-worker.PNG)


