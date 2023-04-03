# Maintenance

This project is here to help maintain Drupal & Composer projects by providing
common tools for cleaning up codebases.

> I go through the same 10-20 steps on every project I get to bring it up to speed.
> There must be a way to get my life back.
>   - @jonpugh

## Features


  1. Provides generic documentation for maintaining composer projects.
  2. Provides boilerplate code for reference, such as common composer.json configs.

### TODO: 
 
  3. Provide composer command for executing a list of checks on a project. 
  4. Provide automation to fix things where possible.


## Site Maintenance Checklists

This file will document the tasks needed to get a site into a supportable state.

This will help provide a roadmap for tools to make this process easier.

### Composer

1. Composer Quality
   1. Relevant Project metadata. Remove templated name, description, support, etc.
      - [] Add specific items and examples. 
   2. Update config & extras to match relevant upstream composer project template:'
      - @TODO: List common projects here
   3. Remove vendor and contributed files.
   4. Ensure .gitignores are in place.
   5. Ensure `composer install` does not cause any git changes.

2. Composer Updates
   1. Update locked dependencies. `rm composer.lock && composer i`
   2. `composer require` as many libraries as possible to get latest required version.
   3. `composer remove` libraries that are required by `drupal/vardot_support`.
   4. Remove all patches that do not apply unless required. 
3. Support Package
   1. Move all dependencies to `drupal/vardot_support`. Remove them from parent project to avoid conflicts or accidentally setting a lower version. 
   2. *`composer require` will silently require a lessor version if your project dependencies are set. For example, if `drupal/raven` or `drupal/site_audit` are already installed at a certain version, `drupal/vardot_support:^1.0@dev` will be used instead of `^1.1@dev`.*. 
   3. To find out why a module is requiring the wrong version, try requiring the right one: `composer require drupal/vardot_support:^1.1@dev`. If it fails, composer will tell you why.
   
3. Documentation & README
   1. Define README requirements:
      2. Project summary.
      3. Environments
      4. Teams
      5. Assets
      6. Management
      7. etc.
   2. Replace default README files with relevant project metadata.
      - [ ] Find or create a README generator that can use composer.json metadata.
   3. Create template README file to ensure completeness.

4. Settings.php
   1. @TODO: Come up with a standardization plan. 
5. Drupal
   1. @TODO: Define best practices/quality for Drupal level. 

