# Discord4J

<a href="https://discord4j.com"><img align="right" src="https://raw.githubusercontent.com/Discord4J/discord4j-web/master/public/logo.svg?sanitize=true" width=27%></a>

[![Support Server Invite](https://img.shields.io/discord/208023865127862272.svg?color=7289da&label=Discord4J&logo=discord&style=flat-square)](https://discord.gg/d4j)
[![Maven Central](https://img.shields.io/maven-central/v/com.discord4j/discord4j-core/3.2.svg?style=flat-square)](https://search.maven.org/artifact/com.discord4j/discord4j-core)
[![Javadocs](https://javadoc.io/badge2/com.discord4j/discord4j-core/3.2.8/javadoc.svg?color=blue&style=flat-square)](https://javadoc.io/doc/com.discord4j/discord4j-core/3.2.8)
[![GitHub Workflow Status (branch)](https://img.shields.io/github/actions/workflow/status/Discord4J/Discord4J/gradle.yml?branch=3.2.x&logo=github&style=flat-square)](https://github.com/Discord4J/Discord4J/actions)

Discord4J is a fast, powerful, unopinionated, reactive library to enable quick and easy development of Discord bots for Java, Kotlin, and other JVM languages using the official [Discord Bot API](https://discord.com/developers/docs/intro).

## 🏃 Quick Example

In this example for v3.2, whenever a user sends a `!ping` message the bot will immediately respond with `Pong!`.

Make sure your bot has the **Message Content** intent enabled in your [developer portal](https://discord.com/developers/applications).

```java
public class ExampleBot {

  public static void main(String[] args) {
    String token = args[0];
    DiscordClient client = DiscordClient.create(token);
    GatewayDiscordClient gateway = client.login().block();

    gateway.on(MessageCreateEvent.class).subscribe(event -> {
      Message message = event.getMessage();
      if ("!ping".equals(message.getContent())) {
        MessageChannel channel = message.getChannel().block();
        channel.createMessage("Pong!").block();
      }
    });

    gateway.onDisconnect().block();
  }
}
```

For a full project example, check out our example projects repository [here](https://github.com/Discord4J/example-projects).

## 🔗 Quick Links

* [Javadocs](https://www.javadoc.io/doc/com.discord4j/discord4j-core)
* [Documentation](https://docs.discord4j.com)
* [Example Projects](https://github.com/Discord4J/example-projects)
* [More examples](https://docs.discord4j.com/examples)
* [Gateway Intents](https://discord.com/developers/docs/topics/gateway#gateway-intents)
* [Discord](https://discord.gg/d4j)

## 💎 Benefits

* 🚀 **Reactive** - Discord4J follows the [reactive-streams](http://www.reactive-streams.org/) protocol to ensure Discord bots run smoothly and efficiently regardless of size.

* 📜 **Official** - Automatic rate limiting, automatic reconnection strategies, and consistent naming conventions are among the many features Discord4J offers to ensure your Discord bots run up to Discord's specifications and to provide the least amount of surprises when interacting with our library.

* 🛠️ **Modular** - Discord4J breaks itself into modules to allow advanced users to interact with our API at lower levels to build minimal and fast runtimes or even add their own abstractions.

* ⚔️ **Powerful** - Discord4J can be used to develop any bot, big or small. We offer many tools for developing large-scale bots from [custom distribution frameworks](https://github.com/Discord4J/connect), [off-heap caching](https://github.com/Discord4J/Stores/tree/master/redis), and its interaction with Reactor allows complete integration with frameworks such as Spring and Micronaut.

* 🏫 **Community** - We pride ourselves on our inclusive community and are willing to help whenever challenges arise; or if you just want to chat! We offer help ranging from Discord4J specific problems, to general programming and web development help, and even Reactor-specific questions. Be sure to visit us on our [Discord server](https://discord.gg/d4j)!

## 📦 Installation

* [Creating a new Gradle project with IntelliJ](https://www.jetbrains.com/help/idea/getting-started-with-gradle.html) *(recommended)*
* [Creating a new Maven project with IntelliJ](https://www.jetbrains.com/help/idea/maven-support.html)
* [Creating a new Gradle project with Eclipse](https://www.vogella.com/tutorials/EclipseGradle/article.html#creating-gradle-projects)
* [Creating a new Maven project with Eclipse](https://www.vogella.com/tutorials/EclipseMaven/article.html#exercise-create-a-new-maven-enabled-project-via-eclipse)

### Gradle
```groovy
repositories {
  mavenCentral()
}

dependencies {
  implementation 'com.discord4j:discord4j-core:3.2.8'
}
```

### Gradle Kotlin DSL
```kotlin
repositories {
  mavenCentral()
}

dependencies {
  implementation("com.discord4j:discord4j-core:3.2.8")
}
```

### Maven
```xml
<dependencies>
  <dependency>
    <groupId>com.discord4j</groupId>
    <artifactId>discord4j-core</artifactId>
    <version>3.2.8</version>
  </dependency>
</dependencies>
```

### SBT
```scala
libraryDependencies ++= Seq(
  "com.discord4j" % "discord4j-core" % "3.2.8"
)
```

## 🔀 Discord4J Versions

Discord4J 3.2.x includes simpler and more powerful APIs to build requests, a new entity cache and performance improvements from dependency upgrades. Check our [Migration Guide](https://docs.discord4j.com/migrating-from-v3-1-to-v3-2) for more details.

| Discord4J                                                   | Support          | Gateway/API | Intents                           | Interactions    |
|-------------------------------------------------------------|------------------|-------------|-----------------------------------|-----------------|
| [v3.3.x](https://github.com/Discord4J/Discord4J/tree/master)| In development   | v9          | Mandatory, non-privileged default | Fully supported |
| [v3.2.x](https://github.com/Discord4J/Discord4J/tree/3.2.x) | Current          | v8          | Mandatory, non-privileged default | Fully supported |
| [v3.1.x](https://github.com/Discord4J/Discord4J/tree/3.1.x) | Maintenance only | v6          | Optional, no intent default       | Maintenance only|

See [our docs](https://docs.discord4j.com/versions) for more details about compatibility.

## 🎉 Sponsors

We would like to give a special thanks to all of our sponsors for providing us the funding to continue developing and hosting repository resources as well as driving forward initiatives for community programs. In particular, we would like to give a special shoutout to these wonderful individuals:

* [decyg](https://github.com/d-g-n)
* [nikammerlaan](https://github.com/nikammerlaan)
* [ByteAlex](https://github.com/ByteAlex)
* [Shadorc](https://github.com/Shadorc)

## ⛰️ Large Bots

Here are some real-world examples of large bots using Discord4J:

* [Groovy](https://groovy.bot/) - Was the second-largest bot on Discord, serving music to over 4 million servers before its shutdown in August 2021.
* [ZeroTwo](https://zerotwo.bot/) - An anime multi-purpose bot used in over 1 million servers.
* [DisCal](https://www.discalbot.com/) - Implements Google Calendar into Discord as seamlessly and comprehensively as possible; serving over 21k servers.
* [Shadbot](https://github.com/Shadorc/Shadbot) - A configurable multipurpose bot with music, gambling mini-games, video game stats, and more; serving nearly 12K servers before its shutdown in August 2021.
* [See-Bot](https://seebot.dev) - A Fortnite focused bot with stat tracking, player lookup, mission alerts, and much more; in over 10k servers.

Do you own a large bot using Discord4J? Ask an admin in our Discord or submit a pull request to add your bot to the list!

## ⚛️ Reactive

Discord4J uses [Project Reactor](https://projectreactor.io/) as the foundation for our asynchronous framework. Reactor provides a simple yet extremely powerful API that enables users to reduce resources and increase performance.

```java
public class ExampleBot {

  public static void main(String[] args) {
    String token = args[0];
    DiscordClient client = DiscordClient.create(token);

    client.login().flatMapMany(gateway -> gateway.on(MessageCreateEvent.class))
      .map(MessageCreateEvent::getMessage)
      .filter(message -> "!ping".equals(message.getContent()))
      .flatMap(Message::getChannel)
      .flatMap(channel -> channel.createMessage("Pong!"))
      .blockLast();
  }
}
```

Discord4J also provides several methods to aid in better reactive chain compositions, such as `GatewayDiscordClient#withGateway` and `EventDispatcher#on` with an [error handling](https://docs.discord4j.com/error-handling) overload.

```java
public class ExampleBot {

    public static void main(String[] args) {
        String token = args[0];
        DiscordClient client = DiscordClient.create(token);

        client.withGateway(gateway -> {
            Publisher<?> pingPong = gateway.on(MessageCreateEvent.class, event ->
                    Mono.just(event.getMessage())
                            .filter(message -> "!ping".equals(message.getContent()))
                            .flatMap(Message::getChannel)
                            .flatMap(channel -> channel.createMessage("Pong!")));

            Publisher<?> onDisconnect = gateway.onDisconnect()
                    .doOnTerminate(() -> System.out.println("Disconnected!"));

            return Mono.when(pingPong, onDisconnect);
        }).block();
    }
}
```

## 🧵 Kotlin

By utilizing Reactor, Discord4J has native integration with [Kotlin coroutines](https://kotlinlang.org/docs/reference/coroutines-overview.html) when paired with the [kotlinx-coroutines-reactor](https://github.com/Kotlin/kotlinx.coroutines/tree/master/reactive/kotlinx-coroutines-reactor) library.

```kotlin
val token = args[0]
val client = DiscordClient.create(token)

client.withGateway {
  mono {
    it.on(MessageCreateEvent::class.java)
      .asFlow()
      .collect {
        val message = it.message
        if (message.content == "!ping") {
          val channel = message.channel.awaitSingle()
          channel.createMessage("Pong!").awaitSingle()
        }
      }
  }
}
.block()
```

## 🐛 Common mistakes

### Calling Message#getContent without enabling the Message Content intent
Starting from September 1, 2022, Discord requires bots to enable the "MESSAGE_CONTENT" intent to access the content of messages.
To enable the intent, go to the [Discord Developer Portal](https://discord.com/developers/applications) and select your bot. Then, go to the "Bot" tab and enable the "Message Content" intent.
Then, add the intent to your bot when creating the DiscordClient:
```java
GatewayDiscordClient client = DiscordClient.create(token)
  .gateway()
  .setEnabledIntents(IntentSet.nonPrivileged().or(IntentSet.of(Intent.MESSAGE_CONTENT)))
  .login()
  .block();
```

## 📚 Examples

### 📑 Message Embeds

<img align="right" src="https://user-images.githubusercontent.com/6114565/82622174-b44a5900-9ba2-11ea-9bc1-2f558958f4cb.png" height=420px>

```java
// IMAGE_URL = https://cdn.betterttv.net/emote/55028cd2135896936880fdd7/3x
// ANY_URL = https://www.youtube.com/watch?v=5zwY50-necw
MessageChannel channel = ...
EmbedCreateSpec.Builder builder = EmbedCreateSpec.builder();
builder.author("setAuthor", ANY_URL, IMAGE_URL);
builder.image(IMAGE_URL);
builder.title("setTitle/setUrl");
builder.url(ANY_URL);
builder.description("setDescription\n" +
      "big D: is setImage\n" +
      "small D: is setThumbnail\n" +
      "<-- setColor");
builder.addField("addField", "inline = true", true);
builder.addField("addFIeld", "inline = true", true);
builder.addField("addFile", "inline = false", false);
builder.thumbnail(IMAGE_URL);
builder.footer("setFooter --> setTimestamp", IMAGE_URL);
builder.timestamp(Instant.now());
channel.createMessage(builder.build()).block();
```

### 🏷️ Find Members by Role Name

Users typically prefer working with names instead of IDs. This example will demonstrate how to search for all members that have a role with a specific name.

```java
Guild guild = ...
Set<Member> roleMembers = new HashSet<>();

for (Member member : guild.getMembers().toIterable()) {
  for (Role role : member.getRoles().toIterable()) {
    if ("Developers".equalsIgnoreCase(role.getName())) {
      roleMembers.add(member);
      break;
    }
  }
}

return roleMembers;
```

Alternatively, using Reactor:
```java
Guild guild = ...
return guild.getMembers()
  .filterWhen(member -> member.getRoles()
    .map(Role::getName)
    .any("Developers"::equalsIgnoreCase));
```

### 🎵 Voice and Music

Discord4J provides full support for voice connections and the ability to send audio to other users connected to the same channel. Discord4J can accept any [Opus](https://opus-codec.org/) audio source with LavaPlayer being the preferred solution for downloading and encoding audio from YouTube, SoundCloud, and other providers.

> [!WARNING]  
> The original LavaPlayer is no longer maintained. A new maintained version can be found [here](https://github.com/lavalink-devs/lavaplayer).
> If you need Java 8 support, you can use [Walkyst's LavaPlayer fork](https://github.com/Walkyst/lavaplayer-fork), but it is also no longer maintained!

To get started, you will first need to instantiate and configure an, conventionally global, `AudioPlayerManager`.

```java
public static final AudioPlayerManager PLAYER_MANAGER;

static {
  PLAYER_MANAGER = new DefaultAudioPlayerManager();
  // This is an optimization strategy that Discord4J can utilize to minimize allocations
  PLAYER_MANAGER.getConfiguration().setFrameBufferFactory(NonAllocatingAudioFrameBuffer::new);
  AudioSourceManagers.registerRemoteSources(PLAYER_MANAGER);
  AudioSourceManagers.registerLocalSource(PLAYER_MANAGER);
}
```

Next, we need to allow Discord4J to read from an `AudioPlayer` to an `AudioProvider`.

```java
public class LavaPlayerAudioProvider extends AudioProvider {

  private final AudioPlayer player;
  private final MutableAudioFrame frame;

  public LavaPlayerAudioProvider(AudioPlayer player) {
    // Allocate a ByteBuffer for Discord4J's AudioProvider to hold audio data for Discord
    super(ByteBuffer.allocate(StandardAudioDataFormats.DISCORD_OPUS.maximumChunkSize()));
    // Set LavaPlayer's AudioFrame to use the same buffer as Discord4J's
    frame = new MutableAudioFrame();
    frame.setBuffer(getBuffer());
    this.player = player;
  }

  @Override
  public boolean provide() {
    // AudioPlayer writes audio data to the AudioFrame
    boolean didProvide = player.provide(frame);

    if (didProvide) {
      getBuffer().flip();
    }

    return didProvide;
  }
}
```

Typically, audio players will have queues or internal playlists for users to be able to automatically cycle through songs as they are finished or requested to be skipped over. We can manage this queue externally and pass it to other areas of our code to allow tracks to be viewed, queued, or skipped over by creating an `AudioTrackScheduler`.

```java
public class AudioTrackScheduler extends AudioEventAdapter {

  private final List<AudioTrack> queue;
  private final AudioPlayer player;

  public AudioTrackScheduler(AudioPlayer player) {
    // The queue may be modifed by different threads so guarantee memory safety
    // This does not, however, remove several race conditions currently present
    queue = Collections.synchronizedList(new LinkedList<>());
    this.player = player;
  }

  public List<AudioTrack> getQueue() {
    return queue;
  }

  public boolean play(AudioTrack track) {
    return play(track, false);
  }

  public boolean play(AudioTrack track, boolean force) {
    boolean playing = player.startTrack(track, !force);

    if (!playing) {
      queue.add(track);
    }

    return playing;
  }

  public boolean skip() {
    return !queue.isEmpty() && play(queue.remove(0), true);
  }

  @Override
  public void onTrackEnd(AudioPlayer player, AudioTrack track, AudioTrackEndReason endReason) {
    // Advance the player if the track completed naturally (FINISHED) or if the track cannot play (LOAD_FAILED)
    if (endReason.mayStartNext) {
      skip();
    }
  }
}
```

Currently, Discord only allows 1 voice connection per server. Working within this limitation, it is logical to think of the 3 components we have worked with thus far (`AudioPlayer`, `LavaPlayerAudioProvider`, and `AudioTrackScheduler`) to be correlated to a specific `Guild`, naturally unique by some `Snowflake`. Logically, it makes sense to combine these objects into one, so that they can be put into a `Map` for easier retrieval when connecting to a voice channel or when working with commands.

```java
public class GuildAudioManager {

  private static final Map<Snowflake, GuildAudioManager> MANAGERS = new ConcurrentHashMap<>();

  public static GuildAudioManager of(Snowflake id) {
    return MANAGERS.computeIfAbsent(id, ignored -> new GuildAudioManager());
  }

  private final AudioPlayer player;
  private final AudioTrackScheduler scheduler;
  private final LavaPlayerAudioProvider provider;

  private GuildAudioManager() {
    player = PLAYER_MANAGER.createPlayer();
    scheduler = new AudioTrackScheduler(player);
    provider = new LavaPlayerAudioProvider(player);

    player.addListener(scheduler);
  }

  // getters
}
```

Finally, we need to connect to the voice channel. After connecting you are given a `VoiceConnection` object where you can utilize it later to disconnect from the voice channel by calling `VoiceConnection#disconnect`.

```java
VoiceChannel channel = ...
AudioProvider provider = GuildAudioManager.of(channel.getGuildId()).getProvider();
VoiceConnection connection = channel.join(spec -> spec.setProvider(provider)).block();

// In the AudioLoadResultHandler, add AudioTrack instances to the AudioTrackScheduler (and send notifications to users)
PLAYER_MANAGER.loadItem("https://www.youtube.com/watch?v=dQw4w9WgXcQ", new AudioLoadResultHandler() { /* overrides */ })
```

### ❌ Disconnecting from a Voice Channel Automatically

Typically, after everyone has left a voice channel, the bot should disconnect automatically as users typically forget to disconnect the bot manually. This problem can be solved rather elegantly using a reactive approach over an imperative one as the example below demonstrates.

```java
VoiceChannel channel = ...
Mono<Void> onDisconnect = channel.join(spec -> { /* TODO Initialize */ })
  .flatMap(connection -> {
    // The bot itself has a VoiceState; 1 VoiceState signals bot is alone
    Publisher<Boolean> voiceStateCounter = channel.getVoiceStates()
      .count()
      .map(count -> 1L == count);

    // After 10 seconds, check if the bot is alone. This is useful if
    // the bot joined alone, but no one else joined since connecting
    Mono<Void> onDelay = Mono.delay(Duration.ofSeconds(10L))
      .filterWhen(ignored -> voiceStateCounter)
      .switchIfEmpty(Mono.never())
      .then();

    // As people join and leave `channel`, check if the bot is alone.
    // Note the first filter is not strictly necessary, but it does prevent many unnecessary cache calls
    Mono<Void> onEvent = channel.getClient().getEventDispatcher().on(VoiceStateUpdateEvent.class)
      .filter(event -> event.getOld().flatMap(VoiceState::getChannelId).map(channel.getId()::equals).orElse(false))
      .filterWhen(ignored -> voiceStateCounter)
      .next()
      .then();

    // Disconnect the bot if either onDelay or onEvent are completed!
    return Mono.first(onDelay, onEvent).then(connection.disconnect());
  });
```
