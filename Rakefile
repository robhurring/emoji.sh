require 'active_record'

class CharacterDB
  PATH = "/System/Library/Input Methods/CharacterPalette.app/Contents/Resources/CharacterDB.sqlite3"
  EMOJI_START = 48756
  EMOJI_SIZE = 635

  def self.emojis
    Character.offset(EMOJI_START).limit(EMOJI_SIZE)
  end
end

class Character < ActiveRecord::Base
  INFO_SEPARATOR = '|'
  self.table_name = 'unihan_dict'

  def readonly?
    true
  end

  def data
    info.split(INFO_SEPARATOR)
  end

  def to_name
    data.first.gsub(/(\s|\W)/, '_').squeeze('_')
  end
end

namespace :emoji do
  task :db do
    ActiveRecord::Base.establish_connection(
      "adapter" => "sqlite3",
      "database"  => CharacterDB::PATH
    )
  end

  desc 'Spit out a list of emojis'
  task :export, [:prefix] => :db do |t, args|
    prefix = args[:prefix]
    prefix = prefix ? %{#{prefix.upcase}_} : ''

    CharacterDB.emojis.each do |chr|
      puts %{export #{prefix}#{chr.to_name}="#{chr.uchr}"}
    end
  end
end

