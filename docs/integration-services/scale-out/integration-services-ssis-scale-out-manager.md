---
title: SQL Server Integration Services Scale Out Manager | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84fe58d4dc7894728c43cb19d17d3444b5b84820
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-scale-out-manager"></a>Integration Services Scale Out Manager

Scale Out Manager est un outil de gestion qui vous permet de gérer la totalité de votre topologie SSIS Scale Out à un seul endroit. Vous n’avez plus besoin de recourir à plusieurs machines et à des commandes TSQL. 

Vous pouvez lancer Scale Out Manager de deux façons.

## <a name="1-open-scale-out-manager-from-sql-server-management-studio"></a>1. Ouvrir Scale Out Manager à partir de SQL Server Management Studio
Ouvrez SQL Server Management Studio et connectez-vous à l’instance SQL Server de Scale Out Master.

Cliquez avec le bouton droit sur **SSISDB** dans l’Explorateur d’objets et sélectionnez **Gérer Scale Out**. ![Gérer Scale Out](media/manage-scale-out.PNG)

> [!NOTE]
> Nous vous recommandons d’exécuter SQL Server Management Studio en tant qu’administrateur, car certaines opérations de gestion Scale Out telles que l’ajout d’un Scale Out Worker nécessitent un privilège administratif.


## <a name="2-open-scale-out-manager-by-runing-ismanagerexe-directly"></a>2. Ouvrir Scale Out Manager en exécutant ISManager.exe directement

ISManager.exe se trouve sous %SystemDrive%\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn\Management. Cliquez avec le bouton droit sur **ISManager.exe** et sélectionnez « Exécuter en tant qu’administrateur ». 

Après son ouverture, vous devez entrer le nom du serveur SQL Server de Scale Out Master et vous y connecter avant de gérer Scale Out.

![Connexion au portail](media/portal-connect.PNG)

Scale Out Manager offre diverses fonctionnalités, comme indiqué ci-dessous. 

## <a name="enable-scale-out"></a>Activer Scale Out
Après vous être connecté à SQL Server, si Scale Out n’est pas activé, vous pouvez cliquer sur le bouton « Activer » pour l’activer.

![Portail - Activer Scale Out](media/portal-enable-scale-out.PNG) 
## <a name="view-scale-out-master-status"></a>Afficher l’état de Scale Out Master
L’état de Scale Out Master apparaît dans la page **Tableau de bord**.

![Portail - Tableau de bord](media/portal-dashboard.PNG)
## <a name="view-scale-out-worker-status"></a>Afficher l’état de Scale Out Worker
L’état de Scale Out Worker apparaît dans la page **Gestionnaire de workers**. Vous pouvez cliquer sur chaque Worker pour connaître son état.

![Portail - Gestionnaire de workers](media/portal-worker-manager.PNG)

## <a name="add-scale-out-worker"></a>Ajouter Scale Out Worker
Pour ajouter un Scale Out Worker, cliquez sur le bouton « + » en bas de la liste Scale Out Worker. 

Entrez le nom de la machine du Scale Out Worker que vous souhaitez ajouter, puis cliquez sur « Valider ». Scale Out Manager vérifie si l’utilisateur actuel a accès aux magasins de certificats sur les machines hébergeant Scale Out Master et Scale Out Worker.

![Connecter le nœud Worker](media/connect-worker.PNG)

Si la validation réussit, Scale Out Manager tente de lire le fichier de configuration du Worker et d’obtenir l’empreinte du certificat de ce dernier. Pour plus d’informations, consultez [Scale Out Worker](integration-services-ssis-scale-out-worker.md). S’il n’est pas en mesure de lire le fichier de configuration du Worker, vous disposez de deux autres méthodes pour fournir le certificat du Worker. 

Vous pouvez entrer l’empreinte du certificat du Worker directement 

![Certificat Worker 1](media/portal-cert1.PNG)

ou fournir le fichier de certificat. 

![Certificat Worker 2](media/portal-cert2.PNG)

Une fois toutes les informations collectées, Scale Out Manager indique les actions à effectuer. Généralement, ces actions incluent l’installation du certificat, la mise à jour du fichier de configuration du Worker et le redémarrage du service Worker. 

![Portail - Ajouter, confirmer 1](media/portal-add-confirm1.PNG)

Si le certificat Worker n’est pas accessible, vous devez le mettre à jour manuellement et redémarrer le service Worker.

![Portail - Ajouter, confirmer 2](media/portal-add-confirm2.PNG)

Cochez la case de confirmation pour pouvoir entamer la procédure d’ajout de Scale Out Worker.

## <a name="delete-scale-out-worker"></a>Supprimer Scale Out Worker
Pour supprimer un Scale Out Worker, sélectionnez-le, puis cliquez sur le bouton « - » situé en bas de la liste Scale Out Worker.


## <a name="enabledisable-scale-out"></a>Activer/désactiver Scale Out
Pour activer ou désactiver un Scale Out Worker, sélectionnez-le, puis cliquez sur le bouton « Activer le Worker » ou « Désactiver le Worker ». L’état du Worker dans Scale Out Manager change en conséquence si le Worker n’est pas hors connexion.

## <a name="edit-scale-out-worker-description"></a>Modifier la description d’un Scale Out Worker
Pour modifier la description d’un Scale Out Worker, sélectionnez-le, puis cliquez sur le bouton « Modifier ». Une fois que vous avez terminé, cliquez sur le bouton « Enregistrer ».

![Portail - Enregistrer le Worker](media/portal-save-worker.PNG)

