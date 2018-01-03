---
title: "Certificat PDW (système de plateforme Analytique) d’approvisionnement"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "La page Configuration de certificats PDW du Gestionnaire de Configuration système Analytique plateforme importe ou supprime le certificat utilisé par PDW."
ms.date: 01/05/2017
ms.topic: article
ms.assetid: 0a423b7d-c6ea-45c1-80b0-26758170594c
caps.latest.revision: "22"
ms.openlocfilehash: c6cbaf559e51103648a4238245d44425c4d5af77
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="pdw-certificate-provisioning"></a>Configuration de certificats PDW
Le **fourniture des certificats PDW** page du système de plateforme Analytique**Configuration Manager** importe ou supprime le certificat utilisé par PDW. 

Un certificat pour chiffrer les connexions peut aider à une communication sécurisée au nœud de contrôle via les clients de SQL Server, les outils qui utilisent les pilotes SQL Server PDW, le [Console d’administration](monitor-the-appliance-by-using-the-admin-console.md), et charge les Services d’intégration. 
  
## <a name="prerequisites"></a>Prerequisites  
Avant d’installer le certificat, procédez comme suit :  
  
1.  Obtenir un certificat de sécurité. Si vous avez besoin de plus d’informations sur la façon d’obtenir un certificat de sécurité, contactez le Support Microsoft.  
  
2.  Enregistrez le certificat sur le nœud de contrôle dans un fichier PFX protégé par mot de passe.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Pour des raisons de sécurité, obtenir un certificat approuvé  
SQL Server PDW prend en charge à l’aide d’un certificat pour chiffrer les connexions au nœud de contrôle ; y compris les connexions à la **Console d’administration**.  
  
Par défaut, le **Console d’administration** inclut un certificat auto-signé qui fournit la confidentialité, mais pas l’authentification du serveur. Cela peut exposer les communications vulnérable à une attaque de man-in-the-middle. Lorsqu’un utilisateur se connecte à la Console d’administration en utilisant le certificat auto-signé, Internet Explorer renvoie l’erreur : « Il existe un problème avec le certificat de sécurité de ce site Web ».  
  
Bien que la connexion via le certificat auto-signé chiffre les données en vol entre le client et le serveur, la connexion est toujours exposé à des personnes malveillantes.  
  
> [!WARNING]  
> Les administrateurs de matériel doivent immédiatement acquérir un certificat lié à une autorité de certification de confiance reconnue par les clients, afin de disposer d’une connexion sécurisée et de supprimer l’erreur qui signale d’Internet Explorer.  
  
Le chemin d’accès de certification doit contenir le nom de domaine complet qui est mappé au nœud de contrôle adresse IP du Cluster (recommandé) ou le nom que les utilisateurs tapent dans la barre d’adresse de leur navigateur pour accéder à la **Console d’administration**.  
  
Utiliser le système de plateforme Analytique**Configuration Manager** pour ajouter ou supprimer le certificat de confiance. Directement à l’aide de l’outil de Configuration de Microsoft Windows HTTP Services de certificat (**winHttpCertCfg.exe**) pour gérer le certificat non pris en charge.  
  
## <a name="import-or-remove-the-certificate"></a>Importer ou de supprimer le certificat  
Les instructions suivantes indiquent comment importer ou de supprimer le certificat de l’appliance.  
  
### <a name="to-import-the-certificate"></a>Pour importer le certificat  
  
1.  Lancer le **Configuration Manager**.  
Pour plus d’informations, consultez [lance le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41; ](launch-the-configuration-manager.md).  

2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **importer un certificat et le configurer pour utiliser**, puis cliquez sur **Parcourir** pour rechercher et sélectionner le fichier de certificat.  
  
4.  Entrez le mot de passe pour le certificat dans le **mot de passe** champ.  
  
5.  Cliquez sur **appliquer** pour configurer le certificat de l’appareil.  
  
SQL Server PDW ne chiffre pas la connexion actuelle à l’aide du certificat importé, mais utilise le certificat pour les nouvelles connexions.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Pour supprimer le certificat précédemment importé  
  
1.  Lancer le **Configuration Manager**. 

<!-- MISSING LINKS
For more information, see [Launch the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager-analytics-platform-system.md).  
-->
  
2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **supprimer tout certificat configuré dans l’appliance**.  
  
4.  Cliquez sur **appliquer** pour supprimer le certificat précédemment importé à partir de l’application.  
  
SQL Server PDW continuera à chiffrer les connexions en cours, mais n’utilise pas la suppression du certificat pour les nouvelles connexions.  
  
![Certificat PDW des appliances DWConfig](media/dwconfig-appl-pdw-cert.png "certificat PDW des appliances DWConfig")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41;](launch-the-configuration-manager.md)  
