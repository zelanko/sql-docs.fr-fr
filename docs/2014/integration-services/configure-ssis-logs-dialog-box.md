---
title: Configurer la boîte de dialogue des journaux SSIS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dbba1b7712bcbdccc821e419b3101065c3164913
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834565"
---
# <a name="configure-ssis-logs-dialog-box"></a>Configurer les journaux SSIS (boîte de dialogue)
  Utilisez la boîte de dialogue **Configurer les journaux SSIS** pour définir les options de journalisation d’un package.  
  
 **Que voulez-vous faire ?**  
  
1.  [Ouvrir la boîte de dialogue Configurer les journaux SSIS](#open_dialog)  
  
2.  [Configurer les options du volet Conteneurs](#container)  
  
3.  [Configurer les options sous l'onglet Fournisseurs et journaux](#provider)  
  
4.  [Configurer les options sous l'onglet Détails](#detail)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Configurer les journaux SSIS  
 **Pour ouvrir la boîte de dialogue Configurer les journaux SSIS**  
  
-   Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , dans le menu **SSIS** , cliquez sur **Enregistrement** .  
  
##  <a name="container"></a> Configurer les options du volet Conteneurs  
 Utilisez le volet **Conteneurs** de la boîte de dialogue **Configurer les journaux SSIS** pour activer l’enregistrement du fichier journal du package et de ses conteneurs.  
  
### <a name="options"></a>Options  
 **Conteneurs**  
 Activez les cases à cocher dans la vue hiérarchique pour activer l'enregistrement du fichier journal du package et de ses conteneurs :  
  
-   Si la case à cocher est désactivée, l'enregistrement du container dans le fichier journal n'est pas activé. Activez-la pour permettre l'enregistrement.  
  
-   Si elle est grisée, le conteneur utilise les options d'enregistrement dans le journal de son parent. Cette option n'est pas disponible pour le package.  
  
-   Si elle est activée, le conteneur définit ses propres options d'enregistrement dans le journal.  
  
 Si un conteneur est grisé alors que vous voulez définir ses options d'enregistrement dans le journal, cliquez sur sa case à cocher deux fois. Le premier clic désactive la case à cocher et le deuxième l'active, vous permettant ainsi de choisir le module fournisseur d'informations à utiliser et de sélectionner les informations à enregistrer.  
  
##  <a name="provider"></a> Configurer les options sous l'onglet Fournisseurs et journaux  
 Utilisez l’onglet **Fournisseurs et journaux** de la boîte de dialogue **Configurer les journaux SSIS** pour créer et configurer des journaux permettant de capturer des événements à l’exécution.  
  
### <a name="options"></a>Options  
 **Type de fournisseur**  
 Sélectionnez un type de module fournisseur d'informations dans la liste.  
  
 **Ajouter**  
 Ajoutez un journal du type spécifié à la collection de modules fournisseurs d'informations du package.  
  
 **Nom**  
 Activez ou désactivez les journaux pour les conteneurs ou les tâches sélectionnés dans le volet **Conteneurs** de la boîte de dialogue **Configurer les journaux SSIS** à l’aide des cases à cocher. Le champ de nom est modifiable. Utilisez le nom par défaut du fournisseur ou tapez un nom descriptif unique.  
  
 **Description**  
 Le champ de description est modifiable. Cliquez sur cette option, puis modifiez la description par défaut du journal.  
  
 **Configuration**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou cliquez sur \<**Nouvelle connexion**> pour créer un gestionnaire de connexions. En fonction du type de module fournisseur d'informations, vous pouvez configurer un gestionnaire de connexions OLE DB ou un gestionnaire de connexions de fichiers. Le module fournisseur d’informations du journal des événements [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows ne nécessite aucune connexion.  
  
 Rubriques connexes : [Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md) , [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md)  
  
 **Supprimer**  
 Sélectionnez un module fournisseur d’informations, puis cliquez sur **Supprimer**.  
  
##  <a name="detail"></a> Configurer les options sous l'onglet Détails  
 Utilisez l’onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS** pour spécifier les événements à enregistrer dans le journal et les détails des informations à consigner. Les informations sélectionnées s'appliquent à tous les modules fournisseurs d'informations du package. Par exemple, vous ne pouvez pas écrire d’informations dans l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et écrire des informations différentes dans un fichier texte.  
  
### <a name="options"></a>Options  
 **Événements**  
 Activez ou désactivez les événements à enregistrer dans le journal.  
  
 **Description**  
 Affichez la description de l'événement.  
  
 **Avancé**  
 Sélectionnez ou désélectionnez les événements à enregistrer dans le journal et les informations à enregistrer pour chaque événement. Cliquez sur **Simple** pour masquer tous les détails de l’enregistrement dans le journal à l’exception de la liste des événements. Les informations suivantes peuvent être enregistrées dans le journal :  
  
|Value|Description|  
|-----------|-----------------|  
|**Ordinateur**|Nom de l'ordinateur sur lequel s'est produit l'événement enregistré.|  
|**Opérateur**|Nom de l'utilisateur qui a démarré le package.|  
|**SourceName**|Nom du package, du conteneur ou de la tâche dans lequel s'est produit l'événement enregistré.|  
|**SourceID**|GUID (Global Unique IDentifier) du package, du conteneur ou de la tâche dans lequel s'est produit l'événement enregistré.|  
|**ExecutionID**|GUID de l'instance d'exécution du package.|  
|**MessageText**|Un message associé à l'entrée de journal.|  
|**DataBytes**|Réservé pour un usage ultérieur.|  
  
 **Simple**  
 Sélectionnez ou désélectionnez les événements à enregistrer dans le journal. Cette option masque les détails d'enregistrement à l'exception de la liste des événements. Si vous sélectionnez un événement, tous les détails d'enregistrement dans le journal sont sélectionnés pour l'événement par défaut. Cliquez sur **Avancé** pour afficher tous les détails d’enregistrement.  
  
 **Load**  
 Spécifiez un fichier XML existant à utiliser comme modèle de configuration des options d'enregistrement dans le journal.  
  
 **Enregistrer**  
 Enregistrez les détails de la configuration en tant que modèle dans un fichier XML.  
  
  
