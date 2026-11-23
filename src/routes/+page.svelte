<script>
  import eventLogo from "#lib/assets/logo.svg";
  import personPortalIcon from "#lib/assets/personPortal.svg";
  import arrowIcon from "#lib/assets/arrow.svg";
  import laptopIcon from "#lib/assets/laptop.svg";
  import plusIcon from "#lib/assets/plus.svg";

  const settings = [
    { title: "General", description: "Define Attendee types & attributes" },
    {
      title: "Title",
      description:
        "Description that explains the value goes here. Description that explains the value goes here.",
    },
    {
      title: "Title",
      description:
        "Description that explains the value goes here. Description that explains the value goes here.",
    },
  ];

  const workflows = [
    {
      title: "Attendee Registration",
      description: "Start by creating a general registration workflow",
    },
    {
      title: "Attendee Registration",
      description: "Start by creating a general registration workflow",
    },
    {
      title: "Attendee Registration",
      description: "Start by creating a general registration workflow",
    },
  ];
</script>

<div class="page">
  <header class="event-header">
    <img src={eventLogo} alt="" width="95" height="95" />
    <div class="event-title">
      <h1>RainFocus Summit</h1>
      <div class="event-meta">
        <p>December 15th</p>
        <p>Lehi, Utah</p>
      </div>
    </div>
    <button class="button" type="button">Edit event</button>
  </header>

  <section class="intro">
    <h2>Event setup guide</h2>
    <p>
      See the available list of modules below. We suggest that you start with
      the attendee module.
    </p>
  </section>

  <section class="module">
    <div class="module-header">
      <img src={personPortalIcon} alt="" width="35" height="35" />
      <h3>Attendee</h3>
    </div>

    <div class="step">
      <p class="step-label"><strong>Step 1:</strong> Base settings.</p>
      <ul class="settings">
        {#each settings as setting}
          <li class="setting">
            <h4 class="title">{setting.title}</h4>
            <p class="description">{setting.description}</p>
          </li>
        {/each}
      </ul>
    </div>

    <div class="step">
      <p class="step-label">
        <strong>Step 2:</strong> Build registration workflows.
      </p>
      <ul class="cards">
        {#each workflows as workflow}
          <li class="card">
            <div class="card-header">
              <img class="icon" src={arrowIcon} alt="" width="24" height="24" />
              <h4 class="title">{workflow.title}</h4>
            </div>
            <p class="description">{workflow.description}</p>
          </li>
        {/each}
        <li>
          <button class="card add-card" type="button">
            <img class="icon" src={plusIcon} alt="" width="24" height="24" />
            Add Registration Workflow
          </button>
        </li>
      </ul>
    </div>

    <div class="step">
      <p class="step-label">
        <strong>Step 3:</strong> Design post-registration experiences.
      </p>
      <ul class="cards">
        <li class="card">
          <div class="card-header">
            <img class="icon" src={laptopIcon} alt="" width="24" height="24" />
            <h4 class="title">Attendee Portal</h4>
          </div>
          <p class="description">
            Manage the portal that attendees will see after they've register for
            your event.
          </p>
        </li>
      </ul>
    </div>
  </section>
</div>

<style lang="scss">
  .page {
    display: flex;
    flex-direction: column;
    gap: 40px;
  }

  .event-header {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    gap: 16px;
  }

  .event-title {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 8px;

    h1 {
      font-size: 32px;
      font-weight: 300;
      color: var(--color-text-header);
    }
  }

  .event-meta p,
  .intro p {
    font-size: 16px;
    line-height: 24px;
  }

  .button {
    flex-shrink: 0;
    padding: 8px 16px;
    border: 0;
    border-radius: 4px;
    background: var(--color-grape);
    color: var(--color-white);
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
  }

  .intro {
    display: flex;
    flex-direction: column;
    gap: 16px;

    h2 {
      font-size: 24px;
      font-weight: 600;
      color: var(--color-text-header);
    }
  }

  .module {
    display: flex;
    flex-direction: column;
    gap: 24px;
    padding-top: 23px;
    border-top: 1px solid var(--color-border);
  }

  .module-header {
    display: flex;
    align-items: center;
    gap: 24px;

    h3 {
      font-size: 20px;
      font-weight: 600;
      color: var(--color-text-header);
    }
  }

  .step {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .step-label {
    font-size: 14px;
    color: var(--color-g3);

    strong {
      font-weight: 700;
      color: var(--color-text-header);
    }
  }

  .title {
    font-size: 13px;
    font-weight: 700;
    color: var(--color-text-header);
  }

  .description {
    max-width: 270px;
    font-size: 12px;
  }

  .icon {
    width: 24px;
    height: 24px;
    object-fit: none;
  }

  .settings {
    display: flex;
    flex-wrap: wrap;
    gap: 16px 32px;
    min-height: 120px;
    padding: 15px 23px;
    border: 1px solid var(--color-border);
    border-radius: 4px;
  }

  .setting {
    display: flex;
    flex-direction: column;
    gap: 4px;
    width: 221px;
    padding: 8px;
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px 24px;
  }

  .card {
    display: flex;
    flex-direction: column;
    gap: 4px;
    min-height: 120px;
    padding: 23px 31px;
    border: 1px solid var(--color-border);
    border-radius: 4px;
  }

  .card-header {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .add-card {
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background: none;
    font-size: 12px;
    color: var(--color-text-header);
    cursor: pointer;
  }

  @media (max-width: 1279px) {
    .cards {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 699px) {
    .cards {
      grid-template-columns: 1fr;
    }
  }

  @media (max-width: 599px) {
    .settings,
    .card {
      padding: 15px;
    }
  }
</style>
