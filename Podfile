swift_version = "4"
workspace 'MVVM-Template'
use_frameworks!

# ignore all warnings from all pods
inhibit_all_warnings!


def sharedPods
  pod 'Alamofire'
  pod 'SwiftyJSON'
  pod 'SnapKit', '~> 3.2.0'
  pod 'ReactiveSwift', '~> 2.0'
  pod 'ReactiveCocoa', '~> 6.0'
end

def testingPods
    pod 'Quick', '~> 1.1'
    pod 'Nimble', '~> 7.0'
end


# MARK: - Project

target 'MVVM-Template' do
  sharedPods
  project 'MVVM-Template/MVVM-Template.xcodeproj'
end


# MARK: - Testing

target 'MVVM-TemplateTests' do
    sharedPods
    testingPods
    project 'MVVM-Template/MVVM-Template.xcodeproj'
end

# MARK: - Utility

post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            if config.name == 'Debug'
                config.build_settings['OTHER_SWIFT_FLAGS'] ||= ['$(inherited)', '-D DEBUG']
            end
        end

      oldSwiftTargets = ['ReactiveCocoa', 'SnapKit', 'Nimble', 'Quick']
  
      installer.pods_project.targets.each do |target|

        podName = target.name.split('-')[0]
        if oldSwiftTargets.include? podName
          target.build_configurations.each do |config|
            config.build_settings['SWIFT_VERSION'] = '3.2'
          end
        end
        
      end

    end
end

