---
title: Notes de publication du plug-in Mixed Reality OpenXR
description: Restez informé des dernières notes de publication et mises à niveau vers le plug-in Mixed Reality OpenXR.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: à jour, outils, prise en main, principes de base, unity, visual studio, toolkit, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, installation, Windows, HoloLens, émulateur, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394628"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="c8ae0-104">Notes de publication du plug-in Mixed Reality OpenXR</span><span class="sxs-lookup"><span data-stu-id="c8ae0-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="c8ae0-105">1.0.0 - Version actuelle</span><span class="sxs-lookup"><span data-stu-id="c8ae0-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="c8ae0-106">Correction d’un bogue où XRAnchorSubsystem démarrait toujours au lancement de l’application, peu importe si ARAnchorManager était présent.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="c8ae0-107">Correction d’un bogue où le mode de reprojection ne fonctionnait pas correctement.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="c8ae0-108">1.0.0-preview.2 - 14/06/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="c8ae0-109">Dépend du plug-in 1.2.2 OpenXR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="c8ae0-110">Modification des fonctionnalités de communication à distance holographique dans des groupes de fonctionnalités individuels.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="c8ae0-111">Correction d’un bogue où « Appliquer les paramètres du projet HoloLens 2 » modifie l’espace de couleurs du projet.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="c8ae0-112">Cela n’est plus nécessaire après le plug-in Unity OpenXR 1.2.0.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="c8ae0-113">Correction d’un bogue dans lequel un appareil d’entrée se connecte sans se déconnecter après la mise en pause et la reprise de l’application.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="c8ae0-114">Ajout de la prise en charge de la détection des plug-ins et états de suivi actuels via ARSession.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="c8ae0-115">Correction d’un bogue dans lequel le préfabriqué ARFoundation « Plan AR par défaut » n’était pas visible.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="c8ae0-116">1.0.0-preview.1 - 02/06/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="c8ae0-117">Prend en charge les extensions MSFT de compréhension des scènes OpenXR au lieu des extensions préliminaires.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="c8ae0-118">La détection de plan sur HoloLens 2 ne requiert plus les versions préliminaires des runtimes Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="c8ae0-119">0.9.5 - 21/05/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="c8ae0-120">Dépend du plug-in 1.2.0 OpenXR d’Unity</span><span class="sxs-lookup"><span data-stu-id="c8ae0-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="c8ae0-121">Adapté à la nouvelle interface utilisateur des fonctionnalités (dans le plug-in OpenXR 1.2.0) pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="c8ae0-122">Correction d’un bogue dans lequel l’inscription du fournisseur de caméras localisables n’a pas été correctement annulée.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="c8ae0-123">Nettoyage de certaines utilisations supplémentaires de [Preserve].</span><span class="sxs-lookup"><span data-stu-id="c8ae0-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="c8ae0-124">Mise à jour du nom « Contrôleur HP Reverb G2 (OpenXR) » dans l’interface utilisateur du système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="c8ae0-125">0.9.4 - 20/05/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="c8ae0-126">Dépend du plug-in 1.2.0 OpenXR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="c8ae0-127">Ajout d’une nouvelle API C# pour obtenir le modèle glTF du contrôleur de mouvement.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="c8ae0-128">Ajout d’une nouvelle API C# pour obtenir les configurations d’affichage activées et définir les paramètres de reprojection.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="c8ae0-129">Ajout d’une nouvelle API C# pour définir des paramètres supplémentaires pour le calcul de maillages avec XRMeshSubsystem.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="c8ae0-130">Ajout d’une nouvelle API C# pour configurer les événements de reconnaissance de mouvement et s’y abonner.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="c8ae0-131">Ajout de la boîte de dialogue de paramètres Windows->XR->Editor Remoting.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="c8ae0-132">Ajout de la prise en charge ARM pour les applications HoloLens UWP.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="c8ae0-133">0.9.3 - 29/04/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="c8ae0-134">Correction d’un bogue dans lequel la connexion à distance holographique n’est pas fiable</span><span class="sxs-lookup"><span data-stu-id="c8ae0-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="c8ae0-135">Correction d’un bogue dans lequel les performances de rendu VR sont altérées après la mise à niveau vers le plug-in 1.1.1 OpenXR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="c8ae0-136">0.9.2 - 21/04/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="c8ae0-137">La détection de plan sur HoloLens 2 dans le plug-in version 0.9.1 fonctionne avec la version 105 du runtime préliminaire Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="c8ae0-138">La détection de plan sur HoloLens 2 dans le plug-in version 0.9.2 fonctionne avec la version 106 du runtime préliminaire Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="c8ae0-139">Suppression de certains rappels inutilisés d’InputProvider pour empêcher les appels, tels que XRInputSubsystem.\* GetTrackingOriginMode (qui ne sont pas gérés par notre système d’entrée), de renvoyer des valeurs erronées.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="c8ae0-140">Fractionnement de la version déconseillée de XRAnchorStore dans son propre fichier pour éviter l’avertissement de la console Unity.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="c8ae0-141">0.9.1 - 20/04/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="c8ae0-142">Dépend du plug-in 1.1.1 OpenXR d’Unity.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="c8ae0-143">Ajout de la prise en charge de l’application de communication à distance holographique pour la plateforme UWP.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="c8ae0-144">Correction d’UnityException où XRAnchorStore essayait d’obtenir une instance de paramètres en dehors du thread principal.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="c8ae0-145">0.9.0 - 29/03/2021</span><span class="sxs-lookup"><span data-stu-id="c8ae0-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="c8ae0-146">Ajout de la prise en charge du mappage spatial via XRMeshSubsystem et ARMeshManager.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="c8ae0-147">Ajout d’une nouvelle API C# pour recevoir des handles OpenXR afin de prendre en charge d’autres packages Unity qui utilisent des extensions OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="c8ae0-148">Ajout d’une nouvelle API C# pour l’interopérabilité avec les API Windows.Perception pour prendre en charge d’autres packages Unity qui utilisent des API Perception WinRT.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="c8ae0-149">Suppression de profils d’interaction des fonctionnalités requises dans l’ensemble des fonctionnalités de Windows Mixed Reality afin que les développeurs puissent choisir les contrôleurs de mouvement qu’ils ont testés.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="c8ae0-150">Ajout d’un outil de validation des fonctionnalité de communication à distance de l’éditeur holographique pour aider les utilisateurs à configurer correctement la communication à distance de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="c8ae0-151">Correction d’un bogue où l’éditeur Unity se bloque lors de la fermeture du mode de communication à distance de l’éditeur holographique après un échec de connexion.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="c8ae0-152">Correction d’un bogue où les textures alpha qui n’ont pas été préalablement multipliées conduisent à une altération des performances sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="c8ae0-153">Correction d’un bogue dans lequel le suivi de la main n’était pas correctement localisé lorsque l’origine de la scène était au niveau du sol.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="c8ae0-154">Correction d’un bogue dans lequel le suivi du maillage de la main disparaît une fois la scène fermée et une nouvelle scène chargée.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="c8ae0-155">Correction d’un bogue où le fournisseur de caméras localisables n’a pas été correctement nettoyé.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="c8ae0-156">Modification de l’espace de noms de l’API XRAnchorStore en Microsoft.MixedReality.OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c8ae0-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>