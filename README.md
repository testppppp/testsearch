# encoding: utf-8
module V5
  class Entities::ProjectTiny < Entities::Base
    expose :id, documentation: {type: 'Integer'}
    expose :path, :name
    expose :http_url_to_repo, as: :html_url
    expose :program, using: Entities::ProgramBasic
    expose :namespace, documentation: {type: 'Hash'}

    def namespace
      entity_class = options[:namespace_with] || Entities::NamespaceMini
      entity_class.represent(object.namespace, options)
    end
  end
end
