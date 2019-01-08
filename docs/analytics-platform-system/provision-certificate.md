---
title: Certificat approvisionnement - Analytique Platform System | Microsoft Docs
description: Configuration de certificats dans le système de plateforme d’Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 98fffc189aab674f46030086a8277395e84f7f4d
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399799"
---
# <a name="certificate-provisioning-in-analytics-platform-system"></a>Configuration de certificats dans le système de plateforme d’Analytique
Le **provisionnement du certificat PWD** page du système de plateforme Analytique**Configuration Manager** importe ou supprime le certificat utilisé par PDW. 

À l’aide, un certificat pour chiffrer les connexions peut aider à une communication sécurisée au nœud de contrôle via les clients de SQL Server, les outils qui utilisent les pilotes SQL Server PDW, le [Console d’administration](monitor-the-appliance-by-using-the-admin-console.md), et charge les Services d’intégration. 
  
## <a name="prerequisites"></a>Prérequis  
Avant d’installer le certificat, procédez comme suit :  
  
1.  Obtenir un certificat sécurisé. Si vous avez besoin de plus d’informations sur l’obtention d’un certificat sécurisé, contactez le Support Microsoft.  
  
2.  Enregistrer le certificat sur le nœud de contrôle dans un fichier PFX protégé par mot de passe.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Pour des raisons de sécurité, obtenir un certificat approuvé  
SQL Server PDW prend en charge à l’aide d’un certificat pour chiffrer les connexions au nœud de contrôle ; y compris les connexions à la **Console d’administration**.  
  
Par défaut, le **Console d’administration** inclut un certificat auto-signé qui fournit la confidentialité, mais pas l’authentification du serveur. Cela peut rendre communications vulnérable à une attaque man-in-the-middle. Lorsqu’un utilisateur se connecte à la Console d’administration en utilisant le certificat auto-signé, Internet Explorer retourne l’erreur : « Il est un problème avec le certificat de sécurité de ce site Web ».  
  
Bien que la connexion via le certificat auto-signé chiffre les données en transit entre le client et le serveur, la connexion est toujours exposé à des personnes malveillantes.  
  
> [!WARNING]  
> Les administrateurs de matériel doivent immédiatement acquérir un certificat lié à une autorité de certification approuvée reconnu par les clients, afin de disposer d’une connexion sécurisée et de supprimer l’erreur qui signale d’Internet Explorer.  
  
Le chemin d’accès de certification doit contenir le nom de domaine complet qui mappe au nœud de contrôle adresse IP du Cluster (recommandé) ou le nom que les utilisateurs tapent dans leur barre d’adresse de navigateur pour accéder à la **Console d’administration**.  
  
Utiliser le système de plateforme Analytique**Configuration Manager** pour ajouter ou supprimer le certificat approuvé. Directement à l’aide de l’outil de Configuration de certificat Microsoft Windows HTTP Services (**winHttpCertCfg.exe**) pour gérer le certificat est non pris en charge.  
  
## <a name="import-or-remove-the-certificate"></a>Importer ou de supprimer le certificat  
Les instructions suivantes vous montrent comment importer ou de supprimer le certificat de l’appliance.  
  
### <a name="to-import-the-certificate"></a>Pour importer le certificat  
  
1.  Lancer le **Configuration Manager**.  
Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  

2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **importer un certificat et le configurer pour utiliser**, puis cliquez sur **Parcourir** pour rechercher et sélectionner le fichier de certificat.  
  
4.  Entrez le mot de passe pour le certificat dans le **mot de passe** champ.  
  
5.  Cliquez sur **appliquer** pour configurer le certificat pour l’appliance.  
  
SQL Server PDW ne cryptera pas la connexion actuelle à l’aide du certificat importé, mais utilisera le certificat pour les nouvelles connexions.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Pour supprimer le certificat importé auparavant  
  
1.  Lancer le **Configuration Manager**. 

<!-- MISSING LINKS
For more information, see [Launch the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager-analytics-platform-system.md).  
-->
  
2.  Dans le volet gauche de la **Configuration Manager**, développez **topologie de l’entrepôt de données parallèle**, puis cliquez sur **certificats**.  
  
3.  Sélectionnez **supprimer n’importe quel certificat configuré dans l’appliance**.  
  
4.  Cliquez sur **appliquer** pour supprimer le certificat importé précédemment à partir de l’appliance.  
  
SQL Server PDW continuera à chiffrer les connexions en cours, mais n’utilisera pas le certificat supprimé pour les nouvelles connexions.  
  
![Certificat PDW des appliances DWConfig](media/dwconfig-appl-pdw-cert.png "certificat PDW des appliances DWConfig")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md)  
